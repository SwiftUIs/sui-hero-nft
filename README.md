# sui-hero-nft

## hero

https://github.com/MystenLabs/sui-move-bootcamp/tree/main/E1/hero

这个工程是一个基于 Sui Move 的“英雄（Hero）”NFT系统，主要实现了英雄的铸造、装备武器（剑）等功能。下面是详细讲解：

---

### 1. 工程结构

- `Move.toml`：项目的配置文件，定义了包名、依赖（如 Sui 框架）、地址等信息。
- `sources/hero.move`：核心模块，实现了英雄 NFT 的主要逻辑。
- `sources/blacksmith.move`：锻造模块，实现了武器（剑）的结构和相关方法。

---

### 2. 主要模块与功能

#### hero::hero

- **HERO 结构体**：一个空结构体，用于初始化包。
- **Hero 结构体**：代表一个英雄 NFT，包含唯一 id、生命值（health）、体力（stamina）。
- **mint_hero**：任何人都可以铸造英雄，初始生命值 100，体力 10。
- **equip_sword**：英雄可以装备一把剑，装备后会提升英雄的攻击力（通过剑的 attack 属性）。每个英雄只能装备一把剑，重复装备会报错。
- **sword**：获取英雄当前装备的剑。
- **add_dof**：通用的动态对象字段添加方法，用于给英雄动态添加装备等。
- **health/stamina**：分别返回英雄的生命值和体力。
- **测试相关方法**：如 `init_for_testing`、`uid_mut_for_testing`，用于测试场景。

#### hero::blacksmith

- **Sword 结构体**：代表一把剑，包含唯一 id 和攻击力（attack）。
- **new_sword**：创建一把新的剑，指定攻击力。
- **attack**：返回剑的攻击力。

---

### 3. 依赖与配置

- 依赖了 Sui 官方的 sui-framework，利用了其动态字段、对象等特性。
- 包地址为 `0x0`，可根据实际部署时修改。

---

### 4. 业务流程举例

1. 用户调用 `mint_hero` 铸造一个英雄 NFT。
2. 用户通过 `blacksmith::new_sword` 创建一把剑。
3. 用户调用 `hero::equip_sword` 给英雄装备这把剑。
4. 可以通过 `hero::sword` 查询英雄当前装备的剑。

---

### 5. 特色说明

- 利用 Sui 的动态对象字段（dynamic_object_field），实现了英雄可以动态装备武器，且每个英雄只能装备一把剑。
- 结构清晰，便于扩展（如后续可添加更多装备类型、技能等）。

---

sui cli 测试这个工程

https://docs.google.com/presentation/d/1NH87zVecZz8OJHbnsCyAf-s4M5E6qjPQzfm8NVhFzpM/edit?slide=id.g2c22b504ffa_0_1002#slide=id.g2c22b504ffa_0_1002



## mint-hero

https://github.com/MystenLabs/sui-move-bootcamp/tree/main/E1/mint-hero


Ran tool

Ran tool

Ran tool

Ran tool

Read file: package.json

Read file: src/index.ts

Read file: src/env.ts

Read file: src/suiClient.ts

Read file: src/helpers/mintHeroWithSword.ts

Read file: src/helpers/getSigner.ts

Read file: src/helpers/getAddress.ts

Read file: src/helpers/getHeroSwordIds.ts

Read file: src/helpers/parseCreatedObjectsIds.ts

Read file: src/tests/mintHeroWithSword.test.ts
### 工程结构与功能讲解

#### 1. 项目结构
- `package.json`：定义了依赖、脚本和项目信息。依赖了 Sui 区块链相关库、TypeScript、Jest（测试）等。
- `src/`：主代码目录
  - `index.ts`：入口文件，主要用于打印环境信息。
  - `env.ts`：环境变量加载与校验，确保 SUI 网络、合约包ID、用户密钥等配置正确。
  - `suiClient.ts`：创建 Sui 区块链客户端，用于后续链上交互。
  - `helpers/`：辅助函数目录，包含与 Sui 区块链交互的核心逻辑。
    - `mintHeroWithSword.ts`：核心功能，负责铸造 Hero NFT、Sword NFT，并将 Sword 装备到 Hero 上。
    - `getSigner.ts`/`getAddress.ts`：通过密钥获取签名者和钱包地址。
    - `getHeroSwordIds.ts`：查询 Hero 身上装备的 Sword。
    - `parseCreatedObjectsIds.ts`：解析交易返回，提取新创建的 Hero 和 Sword 的 ID。
  - `tests/`：测试代码目录
    - `mintHeroWithSword.test.ts`：测试完整的“铸造并装备”流程。

#### 2. 主要业务流程
- **环境配置**：通过 `.env` 文件和 `env.ts` 加载并校验 SUI 网络、合约包ID、用户密钥等。
- **区块链客户端**：`suiClient.ts` 通过环境变量创建 Sui 客户端，后续所有链上操作都通过它完成。
- **签名与地址**：`getSigner.ts` 和 `getAddress.ts` 用于从密钥生成签名者和钱包地址，便于后续链上身份认证。
- **核心功能**：
  - `mintHeroWithSword.ts`（待实现）：负责构建、签名并执行一笔交易，完成以下操作：
    1. 铸造 Hero NFT
    2. 铸造 Sword NFT
    3. 将 Sword 装备到 Hero 上
    4. 将 Hero 转给用户
- **辅助功能**：
  - `parseCreatedObjectsIds.ts`（待实现）：从交易返回的对象变更中，提取新创建的 Hero 和 Sword 的 ID。
  - `getHeroSwordIds.ts`（待实现）：根据 Hero 的 ID 查询其装备的 Sword。
- **测试**：
  - `mintHeroWithSword.test.ts`：自动化测试上述完整流程，确保每一步都成功，并验证 Hero 上确实装备了 Sword。

#### 3. 运行与测试
- 运行主程序：`npm run dev`（会打印 Sui 网络信息）
- 运行测试：`npm test`（会执行自动化测试用例）

#### 4. 总结
本工程是一个基于 Sui 区块链的 NFT 铸造与装备演示项目。核心流程是链上铸造 Hero 和 Sword 两种 NFT，并将 Sword 装备到 Hero 上，最后转给用户。项目结构清晰，便于扩展和测试。部分核心逻辑（如 mint 和解析）尚未实现，需补充链上交互细节。




使用 Sui TypeScript SDK 的客户端应用
https://docs-zh.sui-book.com/guides/developer/first-app/client-tssdk/


