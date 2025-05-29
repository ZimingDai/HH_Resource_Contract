# 资源租赁系统

本项目实现了一个基于智能合约的资源租赁系统，支持 CPU、GPU 和内存等资源的管理、租借和归还功能。

## 文件介绍

- **`BAC002.sol`**: 核心合约文件，定义了资源的管理、租借、归还等功能。实现了资源的发行、查询、租借、归还等操作，并支持暂停和恢复合约的功能。
- **`IBAC002.sol`**: 接口文件，定义了与 `BAC002.sol` 合约的交互接口，包括资源查询、租借记录查询等操作。
- **`Register.sol`**: 包含用户和合约地址的注册和验证工具函数，支持资产的注册和管理操作。
- **`Counters.sol`**: 计数器工具库，用于管理增量计数器，跟踪租借记录和资源操作。
- **`Roles.sol`**: 角色管理工具，定义和验证特定角色的权限，如发行者（Issuer）和暂停者（Suspender）。
- **`SafeMath.sol`**: 提供安全的数学运算方法，防止整数溢出、下溢等问题，确保数值运算的安全性。
- **`BAC002Holder.sol`**: 实现了 `IBAC002Receiver` 接口，用于处理资产的转移和接收。

## 函数概览

| 函数名称               | 功能                     | 输入                                                         | 输出                                                         |
| ---------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `issueResource`        | 发行资源给某个用户       | `to: address`, `cpu: uint256`, `gpu: uint256`, `memoryResource: uint256` | 无                                                           |
| `getResourceBalance`   | 查询用户的资源余额       | `owner: address`                                             | `cpu: uint256`, `gpu: uint256`, `memoryResource: uint256`    |
| `leaseResource`        | 租借资源给其他用户       | `fro: address`, `to: address`, `cpu: uint256`, `gpu: uint256`, `memoryResource: uint256`, `duration: uint256` | 无                                                           |
| `returnLeasedResource` | 归还租借的资源           | `leaner: address`, `leaseIndex: uint256`                     | 无                                                           |
| `getLeasedIn`          | 查询租借入的资源记录     | `user: address`                                              | `froms: address[]`, `cpus: uint256[]`, `gpus: uint256[]`, `memoryResources: uint256[]`, `startTimes: uint256[]`, `durations: uint256[]` |
| `getLeasedOut`         | 查询租借出的资源记录     | `owner: address`                                             | `tos: address[]`, `cpus: uint256[]`, `gpus: uint256[]`, `memoryResources: uint256[]`, `startTimes: uint256[]`, `durations: uint256[]` |
| `getLeasedInExpanded`  | 展开查询租借入的资源记录 | `user: address`                                              | `froms: address[]`, `cpus: uint256[]`, `gpus: uint256[]`, `memoryResources: uint256[]`, `startTimes: uint256[]`, `durations: uint256[]` |
| `getLeasedOutExpanded` | 展开查询租借出的资源记录 | `owner: address`                                             | `tos: address[]`, `cpus: uint256[]`, `gpus: uint256[]`, `memoryResources: uint256[]`, `startTimes: uint256[]`, `durations: uint256[]` |
| `isIssuer`             | 检查某地址是否是发行者   | `account: address`                                           | `bool` (返回 true 表示是发行者，false 表示不是发行者)        |

