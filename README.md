# 使用投票机制，决定是否进入”撤销中“状态的Delegation DAO

## 原Repo

本项目，基于这个[代码库](https://github.com/hyd628/delegation-dao-demo.git)，进行改造。

## 编程题（改造要求）

作为一个DAO，我们不应该使用AccessControl和Role来管理权限，而是使用链上治理或投票制来决定什么时候DAO可以进入“撤销中”状态或重置状态。请以此命题来编写DelegationDAO升级版，您可以实现一个简单的链上投票功能或使用现有的投票或治理库。

## 基本思路

1）使用Openzeppelin的Governance库完成投票及治理。
2）DAOGovernor合约：建立一个链上投票机制，可以通过投票来决定DAO是否可以进入“撤销”状态。
3）其他增加相关的合约，包括：Token.sol(投票用代币MTK，需要扩展ERC20Votes)；TimeLock.sol(用于不同意的人在提案执行前退出)；
4) 其他增加或修改的文件包括：test/sample-test.js, 以及helper.config.js
5）将DelegationDAO修改为Ownable合约。其中，修改schedule_revoke()方法为修饰为onlyOwner，此外，由于去除了Admin等角色，所以，需要修改相关系列方法的权限。

## 当前提交完成内容说明

1）已经完成各合约：./contracts/*.sol
2) 测试文件：./test/sample-test.js

## TODO（尚未完成）

1）原库中的前端页面改造，需要增加投票操作的UI；
2）完成完整的测试之后，修改README.md文件，增加详细的操作指南；
4) 以后考虑进一步修改，任何委托质押的Member可以按照质押金额投票。
