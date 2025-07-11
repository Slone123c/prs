# 物理资源调度中心 - 高保真原型

## 项目概述

这是一个为IDC运维工程师设计的DCIM/IT运维系统中"物理资源调度中心"模块的高保真交互原型。该原型完全符合B端产品设计标准，提供了完整的列表页功能。

## 功能特性

### 🎯 核心功能
- **任务管理**：支持物理资源调度任务的创建、编辑、删除
- **智能搜索**：支持按建设单号、业务标题、业务描述、执行时间等字段搜索
- **业务类型分类**：支持上架、下架、割接三种业务类型
- **数据可视化**：彩色状态标签区分不同业务类型

### 🎨 设计特色
- **专业B端设计**：采用现代扁平化设计语言
- **渐变色系**：专业的紫蓝色渐变主题
- **响应式布局**：适配不同屏幕尺寸
- **交互体验**：流畅的动画效果和悬停反馈

### 📋 数据字段
| 字段名称 | 字段类型 | 说明 |
|---------|---------|------|
| 建设单号 | input | 唯一标识符 |
| 业务标题 | input | 任务名称 |
| 业务类型 | radio | 上架/下架/割接 |
| 业务描述 | textarea | 详细描述 |
| 执行时间 | datetime-local | 计划执行时间 |

## 使用方法

### 🚀 快速开始
1. 直接在浏览器中打开 `physical-resource-scheduling.html`
2. 无需任何服务器或额外配置
3. 所有功能均为前端实现，包含模拟数据

### 💼 主要操作
1. **新增任务**：点击左上角"新增调度任务"按钮
2. **搜索功能**：选择搜索字段，输入关键词后点击搜索或按回车
3. **编辑任务**：点击表格行中的"编辑"按钮
4. **删除任务**：点击表格行中的"删除"按钮（会有确认提示）

### 🔍 搜索说明
- **全部字段**：在所有字段中进行模糊搜索
- **特定字段**：仅在选定字段中搜索
- **实时搜索**：支持键盘回车快速搜索

## 技术实现

### 🛠 技术栈
- **HTML5**：语义化标签，良好的可访问性
- **CSS3**：现代样式，渐变色彩，响应式设计
- **原生JavaScript**：无框架依赖，纯净实现

### 📱 响应式设计
- **桌面端**：≥768px，完整功能展示
- **移动端**：<768px，优化的紧凑布局
- **自适应表格**：在小屏幕上保持可读性

### 🎨 设计系统
- **主色调**：#667eea（专业蓝紫）
- **辅助色**：#764ba2（深紫）
- **状态色**：绿色（上架）、橙色（下架）、蓝色（割接）
- **字体**：系统字体栈，确保最佳显示效果

## 数据模拟

系统预置了5条示例数据，展示不同类型的调度任务：
- 服务器上架任务
- 设备下架维护
- 网络割接升级
- 存储扩容
- 环境设备调整

## 浏览器兼容性

- ✅ Chrome 70+
- ✅ Firefox 60+  
- ✅ Safari 12+
- ✅ Edge 79+

## 部署说明

此原型为纯前端实现，可直接：
1. **本地浏览**：双击HTML文件在浏览器中打开
2. **Web服务器**：上传到任意Web服务器
3. **CDN部署**：支持静态文件托管服务

## 设计理念

### 🎯 用户体验
- **直观操作**：符合用户操作习惯的交互流程
- **信息架构**：清晰的信息层次和视觉重点
- **操作反馈**：及时的操作状态反馈

### 🔒 数据安全
- **前端验证**：完整的表单验证机制
- **操作确认**：删除等危险操作需要二次确认
- **数据持久化**：在真实系统中可轻松集成后端API

## 新增调度任务功能

### 🚀 多步骤工作流
已完整实现第一步和第二步功能：

#### 第一步：调度任务登记
- **基础信息**：建设单号、业务类型、业务标题、业务描述
- **时间管理**：执行开始时间、结束时间（带验证）
- **告警控制**：可选择屏蔽相关告警信息
- **附件上传**：支持Excel文档上传
- **批次管理**：动态添加/删除批次号

#### 第二步：设备调度管理 ⭐ **已完成**
- **操作类型块管理**：
  - 可添加多个操作类型块，每个块独立管理
  - 支持复制、删除操作类型块
  - 实时统计总块数和设备数量
- **块级配置**：
  - 操作类型选择：下拉单选（上架、下架）
  - 设备类型选择：多选（服务器、网络设备）
  - 机房选择：下拉单选（A/B/C/D机房）
- **设备信息管理**：
  - 资产编号（手动输入，自动触发SN码和型号填充）
  - SN码、型号名称（自动填充，只读，蓝色背景标识）
  - 机柜选择（下拉选择预设机柜）
  - U位管理（1-42U，支持起始/结束U位，自动填充结束U位）
  - 使用公司选择（下拉选择预设公司）
  - 内网IP、公网IP（实时格式验证，错误高亮显示）
  - SNMP团体名配置（可选字段）
- **设备限制与提醒**：
  - 每个操作类型块最多50台设备
  - 达到上限时按钮禁用并显示警告
- **智能功能**：
  - 资产编号自动填充：输入AS001-AS005可自动填充对应SN码和型号
  - U位智能计算：选择起始U位后自动填充结束U位
  - IP地址实时验证：支持IPv4和IPv6格式检查
  - 完整的表单验证和业务逻辑检查

#### 第三步：链路拓扑调整 ⭐ **新功能**
- **操作类型块**：可添加多个操作类型块，每个块独立管理
- **操作类型选择**：下拉单选（新增、退订）
- **设备类型选择**：多选（服务器、网络设备）
- **机房选择**：下拉单选（A/B/C/D机房）
- **链路信息管理**：
  - 链路基础信息（通道名称、应用类型、链路类型、供应商）
  - A端设备信息（设备编码、端口号、端口模块、PP架上联）
  - Z端设备信息（设备编码、端口号、端口模块、PP架上联）
  - 扩展配置（SID/CID、连接标签编码、国家-城市级联选择）
- **链路限制**：每个操作类型块最多100条链路
- **链路操作**：编辑更多、删除功能

### 🎨 交互特性
- **步骤导航**：清晰的步骤条和进度指示
- **数据联动**：资产编号自动填充SN码和型号信息
- **实时验证**：即时的表单验证和错误提示（IP格式、必填字段等）
- **智能默认**：自动填充结束U位等便捷功能
- **设备管理**：支持设备的增删、操作类型块的复制删除
- **视觉反馈**：自动填充字段蓝色背景标识、验证错误红色高亮
- **数量控制**：设备数量限制和实时统计显示
- **响应式设计**：完美适配移动端设备

### 📊 数据结构
完整的数据收集包括：
```javascript
{
  basicInfo: { /* 第一步基础信息 */ },
  deviceManagement: { 
    operationBlocks: [
      {
        id: number,
        operationType: 'UP'|'DOWN', // 操作类型：上架/下架
        deviceTypes: ['server'|'network'], // 设备类型数组
        room: string, // 机房
        devices: [
          {
            assetId: string, // 资产编号
            sn: string, // SN码（自动填充）
            model: string, // 型号名称（自动填充）
            cabinet: string, // 机柜
            startU: number, // 起始U位（1-42）
            endU: number, // 结束U位（1-42）
            ownerCompany: string, // 使用公司
            privateIp: string, // 内网IP（支持IPv4/IPv6）
            publicIp: string, // 公网IP（支持IPv4/IPv6）
            snmpCommunity: string // SNMP团体名
          }
        ]
      }
    ],
    totalDevices: number,
    totalBlocks: number
  },
  topologyAdjustment: {
    topologyBlocks: [
      {
        id: number,
        operationType: 'ADD'|'CANCEL', // 操作类型：新增/退订
        deviceTypes: ['server'|'network'], // 设备类型数组
        room: string, // 机房
        links: [
          {
            channelName: string, // 所属物理通道名称
            applicationType: 'CUSTOMER'|'ISP'|'REMOTE'|'CABINET', // 应用类型
            linkType: 'FIBER'|'LEASED'|'PATCH', // 链路类型
            supplier: string, // 供应商
            extraConfig: { // 扩展配置
              sidCid: string,
              connectionCode: string,
              country: string,
              city: string
            },
            aEnd: { // A端设备信息
              deviceCode: string,
              portNumber: string,
              portModule: string,
              isPpFrame: boolean
            },
            zEnd: { // Z端设备信息
              deviceCode: string,
              portNumber: string,
              portModule: string,
              isPpFrame: boolean
            }
          }
        ]
      }
    ],
    totalLinks: number,
    totalTopologyBlocks: number
  }
}
```

## 后续扩展

该原型设计时已考虑后续扩展：
- **API集成**：预留接口调用位置
- **权限控制**：可扩展用户权限验证
- **数据分页**：已预留分页控件
- **批量操作**：可扩展批量选择功能
- **导出功能**：可添加数据导出能力
- **工作流优化**：步骤间数据联动和智能推荐
- **设备模板**：预设设备配置模板
- **批量导入**：Excel批量导入设备信息

---

**设计理念**：专业、高效、易用  
**适用场景**：IDC运维管理、设备调度、资源规划  
**技术特色**：无依赖、高性能、易维护、完整工作流、专业B端设计 