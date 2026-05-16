# case-library
# 主图案例参考库 case-library

供主图生图系统在 T1/T3 调取时机使用的参考案例库。

## 目录结构
case-library/
├── index.json # 全量案例索引，供小工具查询
└── cases/
└── {case_id}/
├── {case_id}.jpg # 案例图片
└── {case_id}.json # 画面描述

## 命名规范
ref_{品类英文}{阻力码英文}{序号}
示例：ref_carseat_TSB_safety_001

- 全部小写英文+下划线
- 禁止中文、空格、特殊字符（- 除外用于连接阻力子类）
- 图片、JSON、文件夹三者同名

## 新增案例操作步骤

1. 用「案例入库执行命令」生成 `{case_id}.json`
2. 新建文件夹 `cases/{case_id}/`
3. 上传图片 `{case_id}.jpg` 和描述 `{case_id}.json`
4. 更新根目录 `index.json`：
   - `total` +1
   - `cases` 数组追加新案例摘要对象

## index.json 字段说明

| 字段 | 说明 |
|---|---|
| `case_id` | 唯一编号，与文件夹名一致 |
| `image_url` | jsDelivr CDN 图片访问地址 |
| `json_url` | jsDelivr CDN JSON 访问地址 |
| `category` | 品类中文名 |
| `primary_barrier` | 主阻力码（如 TSB-安全） |
| `dimension_A` | 产品本身 / 产品与人 / 产品与环境 |
| `dimension_B` | 整体全局 / 因果溯源 / 使用过程 / 使用结果 / 食用过程 |
| `skeleton_id` | 布局骨架（S-TOP/S-LEFT/D-TL/T-TLB 等12种） |
| `operating_stage` | 新品冷启动期 / 日销成交期 / 大促爆发期 |
| `has_people` | 是否有人物入镜 |
| `image_ratio` | square（1:1）/ portrait（3:4） |

## case_meta.json 字段说明

详见 `schema_ref`：
- 产品呈现方式_v4.1
- 文案策略执行规则_v1.3
- 布局骨架空间枚举库_v1.1

## CDN 访问地址格式
https://cdn.jsdelivr.net/gh/xingyouchen0127/case-library@main/{文件路径}


