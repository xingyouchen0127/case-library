# case-library
# 主图案例参考库 case-library

供主图生图系统在 T1/T3 调取时机使用的参考案例库。

## 目录结构
case-library/
├── index.json # 全量案例索引，供小工具查询
├── category_map.json # 品类码映射表，AI识别文本→标准code
└── cases/
└── {case_id}/
├── {case_id}.jpg # 案例图片
└── {case_id}.json # 画面描述
## 命名规范
ref_{品类英文}{阻力码英文}{序号}
示例：ref_carseat_TSB_safety_001

- 全部小写英文+下划线
- 禁止中文、空格、特殊字符（`-` 除外用于连接阻力子类）
- 图片、JSON、文件夹三者同名

## 新增案例操作步骤

1. 用「案例入库执行命令」生成 `{case_id}.json`
2. 新建文件夹 `cases/{case_id}/`
3. 上传图片 `{case_id}.jpg` 和描述 `{case_id}.json`
4. 更新根目录 `index.json`：
   - `total` +1
   - `cases` 数组追加新案例摘要对象
5. 如涉及新品类，在 `category_map.json` 的 `categories` 数组追加新品类对象

## index.json 字段说明

| 字段 | 说明 |
|---|---|
| `case_id` | 唯一编号，与文件夹名一致 |
| `image_url` | jsDelivr CDN 图片访问地址 |
| `json_url` | jsDelivr CDN JSON 访问地址 |
| `category_code` | 标准品类码（如 `CHILD_carseat`） |
| `category_label` | 品类中文名（如 `儿童安全座椅`） |
| `primary_barrier` | 主阻力码（如 `TSB-安全`） |
| `dimension_A` | `产品本身` / `产品与人` / `产品与环境` |
| `dimension_B` | `整体全局` / `因果溯源` / `使用过程` / `使用结果` / `食用过程` |
| `skeleton_id` | 布局骨架（`S-TOP` / `S-BTM` / `S-LEFT` / `S-RIGHT` / `D-TL` / `D-TR` / `D-TB` / `D-LR` / `T-TLB` / `T-TRB` / `T-TLR` / `Q-ALL`） |
| `operating_stage` | `seed`（新品种草期）/ `daily`（日销成交期）/ `campaign`（活动爆发期） |
| `has_people` | 是否有人物入镜，`true` / `false` |
| `image_ratio` | `square`（1:1）/ `portrait`（3:4） |

## case_meta.json 字段说明

详见 `schema_ref`：
- 产品呈现方式_v4.1
- 文案策略执行规则_v1.3
- 布局骨架空间枚举库_v1.1
- 经营阶段参数_v1.2

## category_map.json 说明

AI 识别图片输出的品类文本不标准，查询前需先通过 `aliases` 匹配转换为标准 `code`，再用 `code` 检索 `index.json`。

新增品类时在 `categories` 数组追加对象，`aliases` 收录所有 AI 可能输出的近似描述。

## CDN 访问地址格式

