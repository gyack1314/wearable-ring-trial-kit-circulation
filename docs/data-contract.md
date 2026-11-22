# 业务资料契约

所有人物、家庭、设备、供应商和交易均为本地合成资料。金额使用整数分，时长字段的单位写在列说明中。时间戳含时区，起止区间均为左闭右开。空值表示未观察或未提供，数值零保留其真实含义。

allocation 表示拿到试戴机会，wear 没有开始时间表示未佩戴，discomfort 表示因不适提前结束。试戴评分是原始观察，不是可接受尺寸答案。inspection 是后续检查事实，可以与实物主档申报成色不同。

## people.csv

人员主档。第一列是物理记录的唯一键。

- `person` 表示人员编号，类型为 str。
- `household` 表示登记家庭编号，类型为 str。
- `segment` 表示长期客群，类型为 str。
- `home_zone` 表示常居时区，类型为 str。
## allocations.csv

各人拿到试戴环的顺序与机会。第一列是物理记录的唯一键。

- `allocation` 表示分配，类型为 str。
- `person` 表示试戴者，类型为 str。
- `size` 表示尺寸号，类型为 int。
- `material` 表示材质，类型为 str。
- `sequence` 表示试戴顺序，类型为 int。
- `offered` 表示交给时间，类型为 datetime。
- `planned_hours` 表示计划时长，类型为 int。
## wear.csv

实际试戴和退出。第一列是物理记录的唯一键。

- `record` 表示记录，类型为 str。
- `allocation` 表示分配，类型为 str。
- `start` 表示佩戴开始，类型为 datetime，允许空值。
- `end` 表示佩戴结束，类型为 datetime，允许空值。
- `stop_reason` 表示结束原因，类型为 str。
- `contact` 表示传感器接触比例，类型为 float，允许空值。
## feedback.csv

分时段反馈。第一列是物理记录的唯一键。

- `record` 表示反馈，类型为 str。
- `allocation` 表示分配，类型为 str。
- `period` 表示日间或夜间，类型为 str。
- `comfort` 表示舒适度1到5，类型为 int，允许空值。
- `tightness` 表示松紧负2到2，类型为 int，允许空值。
- `received` 表示收到，类型为 datetime。
## material_checks.csv

同一人同尺寸的试戴环与成品材质对照。第一列是物理记录的唯一键。

- `record` 表示对照记录，类型为 str。
- `person` 表示用户，类型为 str。
- `size` 表示尺寸，类型为 int。
- `resin_comfort` 表示试戴环舒适度，类型为 int。
- `metal_comfort` 表示成品舒适度，类型为 int。
- `metal_contact` 表示成品传感器接触比例，类型为 float。
- `at` 表示对照时间，类型为 datetime。
## rings.csv

实物戒指现状。第一列是物理记录的唯一键。

- `ring` 表示实物，类型为 str。
- `owner` 表示持有人，类型为 str。
- `size` 表示尺寸，类型为 int。
- `material` 表示材质，类型为 str。
- `grade` 表示成色，类型为 str。
- `available` 表示最早可交付，类型为 datetime。
- `recall` 表示召回标志，类型为 int。
- `value_cents` 表示声明价值，类型为 int。
## sales.csv

已售实物与保修承诺。第一列是物理记录的唯一键。

- `sale` 表示销售，类型为 str。
- `person` 表示用户，类型为 str。
- `ring` 表示实物，类型为 str。
- `delivered` 表示原交付，类型为 datetime。
- `warranty_end` 表示原保修到期，类型为 datetime。
- `paid_cents` 表示已付，类型为 int。
## requests.csv

换型来源意向。第一列是物理记录的唯一键。

- `request` 表示申请，类型为 str。
- `person` 表示用户，类型为 str。
- `offered_ring` 表示交回实物，类型为 str。
- `max_extra_cents` 表示接受补价上限，类型为 int。
- `wait_days` 表示可等天数，类型为 int。
- `requested` 表示申请时间，类型为 datetime。
- `status` 表示同意状态，类型为 str。
## inspections.csv

回收点的实物检查。第一列是物理记录的唯一键。

- `inspection` 表示检查，类型为 str。
- `ring` 表示实物，类型为 str。
- `grade` 表示实查成色，类型为 str。
- `received` 表示检查时间，类型为 datetime。

数值条款、可调整范围及业务枚举见 data/terms.json。数据契约定义来源记录和已存在的协议，分析方法及内部实现由项目使用者按业务需求选择。
