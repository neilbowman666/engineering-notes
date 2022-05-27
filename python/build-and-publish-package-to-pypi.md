# 打包并发布包到 PyPI

## 安装依赖

```bash
pip3 install setuptools
pip3 install wheel
pip3 install twine
```

## 项目结构

setup.py

```python
from setuptools import setup

setup(
        name='pytest_assume',
        version='1.0.0',
        description='A print test for PyPI',
        author='winsrh',
        author_email='win@163.com',
        url='https://www.python.org/',
        license='MIT',
        keywords='ga nn',
        project_urls={
            'Documentation': 'https://packaging.python.org/tutorials/distributing-packages/',
            'Funding': 'https://donate.pypi.org',
            'Source': 'https://github.com/pypa/sampleproject/',
            'Tracker': 'https://github.com/pypa/sampleproject/issues',
        },
        packages=['pytest_assume'],  # 包名
        python_requires='>=3'
)
```

## 项目打包

1. 打包 tar.gz 源码包

```bash
python setup.py sdist
```

2. 打包 whl 包

```bash
python setup.py bdist_wheel
```

## 取包地址

> /<项目目录>/dist/pytest_assume-1.0.0-py3-none-any.whl
> 
> /<项目目录>/dist/pytest_assume-1.0.0.tar.gz

## 发布到仓库

```bash
twine upload dist/*
```
