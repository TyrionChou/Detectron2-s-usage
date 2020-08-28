# Detectron2-s-usage
Tutorials

5.Use Custom Datasets（使用自定数据集）

12.Configs

Detectron2提供一个基于键值对配置系统，可以用来获得标准的，常见的行为。
Detectron2的配置系统使用YAML和yacs。除了访问和更新配置的基本操作外，我们还提供以下额外功能：
1. 配置有_BASE_：base.yaml域，它将优先加载基础配置。在基础配置中的值会被子配置文件覆盖，不存在冲突情况。我们为标准模型架构提供了一些基础配置。
2. 我们提供了配置版本控制，实现向下兼容。如果你的配置文件使用类似VERSION:2的配置行进行版本控制，即使将来我们更改了一些键，detectron2仍然可以识别它们。
配置文件是有限的。我们不希望detectron2中的所有功能都从配置文件中获得。如果在配置空间中没有您需要的内容，请使用detectron2的API编写代码。

1）基础使用
我们在这里展示CfgNode对象的一些基础使用方法。更对信息从https://detectron2.readthedocs.io/modules/config.html#detectron2.config.CfgNode 中获取。

from detectron2.config import get_cfg
cfg = get_cfg()    # obtain detectron2's default config
cfg.xxx = yyy      # add new configs for your own custom components
cfg.merge_from_file("my_cfg.yaml")   # load values from a file

cfg.merge_from_list(["MODEL.WEIGHTS", "weights.pth"])   # can also load values from a list of str
print(cfg.dump())  # print formatted configs
