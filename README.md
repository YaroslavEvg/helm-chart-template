# Helm Chart Template

This Helm chart is a customizable template for deploying applications on Kubernetes and OpenShift. The chart is structured to allow easy extension and configuration of resources like DeploymentConfigs, Services, Routes, PVCs, Secrets, and ConfigMaps.

## Usage

To use this chart, you need to modify the values in the `values.yaml` file according to your application requirements. Each resource type can be enabled or disabled and configured individually.

### Structure

- **deploymentConfigs**: Deploy your application with specific configurations like image, resources, probes, etc.
- **services**: Define services for your application components.
- **routes**: Expose your services outside the cluster.
- **pvcs**: Provision PersistentVolumeClaims for stateful components.
- **secrets**: Manage sensitive information like passwords and tokens.
- **configMaps**: Store non-confidential data in key-value pairs.
- **service_monitors**: Set up monitoring for your services (Prometheus).

### Enabling Resources

To enable a resource, set `enabled: true` under the corresponding section in the `values.yaml` file.

### Example: Enabling Redis DeploymentConfig

To enable a DeploymentConfig for Redis:

1. Go to the `deploymentConfigs` section in `values.yaml`.
2. Set `enabled: true`.
3. Customize the `items` section with the Redis configuration details.

```yaml
deploymentConfigs:
  enabled: true
  items:
    - name: redis
```

## Extending the Chart
To add new resources:

1. Duplicate an existing section.
2. Modify the new section with the desired configuration.
3. Enable the section by setting enabled: true.

### Customization
Customize resources by modifying their properties under each section. For example, to change the image of a DeploymentConfig:

```yaml
deploymentConfigs:
  ...
  items:
    - name: redis
      namespace: openshift
      image: redis
      image_version: latest
      ...
    - name: my-app
      namespace: eco-service-stage
      image: my-app
      image_version: latest
      ...
```
Remember to always validate your values.yaml file for any syntax or configuration errors before deploying the chart.


---

### README.md (Русский)

# Шаблон Helm Chart

Этот Helm чарт является настраиваемым шаблоном для развертывания приложений в Kubernetes и OpenShift. Чарт структурирован так, чтобы позволить легко расширять и настраивать ресурсы, такие как DeploymentConfigs, Services, Routes, PVCs, Secrets и ConfigMaps.

## Использование

Для использования этого чарта вам необходимо изменить значения в файле `values.yaml` в соответствии с требованиями вашего приложения. Каждый тип ресурса может быть включен или отключен и настроен индивидуально.

### Структура

- **deploymentConfigs**: Развертывание вашего приложения с определенными конфигурациями, такими как образ, ресурсы, пробы и т.д.
- **services**: Определение сервисов для компонентов вашего приложения.
- **routes**: Открытие ваших сервисов за пределы кластера.
- **pvcs**: Создание PersistentVolumeClaims для состояния компонентов.
- **secrets**: Управление чувствительной информацией, такой как пароли и токены.
- **configMaps**: Хранение неконфиденциальных данных в парах ключ-значение.
- **service_monitors**: Настройка мониторинга для ваших сервисов (Prometheus).

### Включение Ресурсов

Для включения ресурса установите `enabled: true` в соответствующем разделе файла `values.yaml`.

### Пример: Включение DeploymentConfig для Redis

Чтобы включить DeploymentConfig для Redis:

1. Перейдите в раздел `deploymentConfigs` в `values.yaml`.
2. Установите `enabled: true`.
3. Настройте раздел `items` с конфигурацией Redis.

```yaml
deploymentConfigs:
  enabled: true
  items:
    - name: redis
      ...
```



## Расширение Чарта
Чтобы добавить новые ресурсы:

1. Скопируйте существующий раздел.
2. Измените новый раздел с желаемой конфигурацией.
3. Включите раздел, установив enabled: true.

### Настройка

Настройте ресурсы, изменяя их свойства в каждом разделе. Например, для изменения образа в DeploymentConfig:

```yaml
deploymentConfigs:
  ...
  items:
    - name: redis
      namespace: openshift
      image: redis
      image_version: latest
      ...
    - name: my-app
      namespace: eco-service-stage
      image: my-app
      image_version: latest
      ...
```
Не забывайте всегда проверять файл values.yaml на наличие синтаксических или конфигурационных ошибок перед развертыванием чарта.
