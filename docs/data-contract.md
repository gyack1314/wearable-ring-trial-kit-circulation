# 业务资料契约

所有人物、家庭、设备、供应商和交易均为本地合成资料。金额使用整数分，时长字段的单位写在列说明中。时间戳含时区，起止区间均为左闭右开。空值表示未观察或未提供，数值零保留其真实含义。

试戴为舒适体验研究。材质对照为独立原始观察，不是偏好答案。rounds记录外部已接受安排，kit_events是后来发生的实物与退出事实。地区Z1到Z3之间按cross_region运输，起止时间均为UTC。新研究方法需说明早退、顺序残留及对照支持范围。

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
## kits.csv

完整试戴套件。第一列是物理记录的唯一键。

- `kit` 表示套件，类型为 str。
- `material` 表示材质，类型为 str。
- `sizes` 表示完整套件包含的尺寸集合，类型为 str。
- `location` 表示当前位置，类型为 str。
- `ready` 表示原定可发出时间，类型为 datetime。
## participation_windows.csv

本人愿意参与的条件。第一列是物理记录的唯一键。

- `record` 表示条件，类型为 str。
- `person` 表示参与者，类型为 str。
- `start` 表示可开始时间，类型为 datetime。
- `end` 表示最迟结束时间，类型为 datetime。
- `region` 表示所在地区，类型为 str。
- `rejected_sizes` 表示本人明确不愿再试的尺寸集合，类型为 str，允许空值。
- `max_rounds` 表示接受总轮次，类型为 int。
## rounds.csv

来源已经接受的试戴安排。第一列是物理记录的唯一键。

- `round` 表示轮次，类型为 str。
- `person` 表示参与者，类型为 str。
- `kit` 表示套件，类型为 str。
- `start` 表示试戴开始，类型为 datetime。
- `end` 表示试戴结束，类型为 datetime。
- `sequence` 表示已接受尺寸顺序，类型为 str。
- `status` 表示来源状态，类型为 str。
## kit_events.csv

退出、回收和完整性检查事实。第一列是物理记录的唯一键。

- `record` 表示事件，类型为 str。
- `kit` 表示套件，类型为 str。
- `round` 表示试戴轮次，类型为 str。
- `at` 表示发生，类型为 datetime。
- `kind` 表示事件类型，类型为 str。
- `present_sizes` 表示回收时实际包含尺寸，类型为 str，允许空值。

数值条款、可调整范围及业务枚举见 data/terms.json。数据契约定义来源记录和已存在的协议，分析方法及内部实现由项目使用者按业务需求选择。
