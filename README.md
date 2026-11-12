# 词元支出变化的精确因素分解

本项目保存高校公共算力与教学研究的虚构汇总资料和Python读取工具。现有工具仅解析输入并显示类型与记录数，不执行统计计算、优化、拟合或训练。样本不代表真实高校、个人或教学成效。

## 资料口径

amount单位为最小货币单位，p为每标准词元金额；model_mix按模型键给定占比。counterfactual_source说明零占比模型的t和p出处，空值表示未知，不自动补0。

fixtures为只读资料目录，src/cost_reader.py为现有读取器，material-index.json记录文件内容摘要。研究结果可以放入独立.workspace-output目录，不要覆盖原始数据。

## 运行与开发

Python 3.11及以上版本；现有读取器只用标准库，无安装步骤。进入项目根目录：

    python -m src.cost_reader fixtures/periods.json

编译检查：

    python -m compileall -q src tests

输入契约测试：

    python -m unittest discover -s tests -v

## 容器环境

    docker build -t token-cost-shapley:local .
    docker run --rm token-cost-shapley:local

镜像按完整摘要固定，默认执行读取测试。容器不需要访问外部教学平台。
