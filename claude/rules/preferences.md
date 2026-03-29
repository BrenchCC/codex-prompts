# Code Style Preferences

## Personalization
- My name: Brench
- Response prefix: Every response must start with "Brench, "

---

## Python Code Conventions

### Assignment Spacing
- `=` must have spaces on both sides
- Applies to: variable assignments, dictionary definitions, function default parameters, keyword arguments
- Preferred: `x = 1`, `func(arg = 1)`, `def f(a = 1):`
- Rejected: `x=1`, `func(arg=1)`, `def f(a=1):`

### Import Organization (3 groups, separated by blank lines)
1. Python Standard Library
2. Third-party/Pip Installed Libraries
3. Local/Custom Modules

Within each group:
1. `import xxx` first
2. `from xxx import xxx` second
3. Sort by line length (shortest to longest)

**Example**:
```python
import os
import sys
import logging
from typing import List, Dict

import torch
import numpy as np
from tqdm import tqdm
from torch.utils.data import DataLoader

import my_module
from utils import my_function
```

### Multi-line Formatting
- `>= 4` elements: one per line
- `< 4` elements: same line
- Applies to: function parameters, function call arguments, dictionary initialization

**Example**:
```python
# < 4 elements, single line
my_dict = {"a": 1, "b": 2}

# >= 4 elements, multi-line
def train_model(
    model,
    optimizer,
    data_loader,
    num_epochs,
    device
):
    pass
```

### Logging
- `logging.basicConfig` only in `if __name__ == "__main__":`
- Instantiate: `logger = logging.getLogger(__name__)` immediately after imports
- Format:
  ```python
  logging.basicConfig(
      level = logging.INFO,
      format = '%(asctime)s - %(name)s - %(levelname)s - %(message)s',
      handlers = [logging.StreamHandler()]
  )
  ```
- Section highlighting: Use decorative characters (`=`, `-`, `*`), avoid standalone `\n`
  ```python
  logger.info("=" * 80)
  logger.info("重要小节开始")
  logger.info("=" * 80)

  logger.info("-" * 60)
  logger.info("数据处理阶段")
  logger.info("-" * 60)

  logger.info("*" * 50)
  logger.info("模型训练开始")
  logger.info("*" * 50)
  ```

### Comments & Documentation
- All comments in English
- Function definitions must have `"""` docstrings explaining each parameter

### Progress Display
- Use `tqdm` for loops

### Argument Parsing
- `argparse` must be wrapped in `def parse_args():`

### Conda Execution
- Ask for Conda environment name before any Python execution
- Execute: `conda run -n <ENV_NAME> python <SCRIPT_PATH>`
- Interactive: `conda run -n <ENV_NAME> python`
- Install: `conda run -n <ENV_NAME> pip install <PACKAGE>`

**Workflow**:
1. Ask: "What Conda environment should I use for this project?"
2. Wait for environment name
3. Execute all Python commands with that environment
