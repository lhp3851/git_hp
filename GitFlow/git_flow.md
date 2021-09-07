# Git Flow

## 1. 初始化

```sh
git flow init
```

## 2. feature

### 2.1 新建

```sh
git flow feature start <feature_name>
```

### 2.2 完成

```sh
git flow feature finish <feature_name>
```

### 2.3 发布

```sh
git flow feature publish <feature_name>
```

### 2.4 获取

```sh
git flow feature pull origin <feature_name>
```

### 2.5 跟踪

```sh
git flow feature track <feature_name>
```

## 3. Releases

### 3.1 新建

```sh
git flow release start <release_name> [<base>]
```

### 3.2 发布

```sh
git flow release publish <release_name>
```

### 3.3 完成

```sh
git flow release finish <release_name>
```

### 3.4 推送 tags

```sh
git push --tags
```

## 4. Bugfixes

### 4.1 新建

```sh
git flow bugfix start <bugfix_name>
```

### 4.2 完成

```sh
git flow bugfix finish <bugfix_name>
```

### 4.3 发布

```sh
git flow bugfix publish <bugfix_name>
```

### 4.4 获取

```sh
git flow bugfix pull origin <bugfix_name>
```

### 4.5 跟踪

```sh
git flow bugfix track <bugfix_name>
```

## 5. Hotfixes

### 5.1 新建

```sh
git flow hotfix start <version_name> [<base_name>]
```

### 5.2 完成

```sh
git flow hotfix finish <version_name>
```
