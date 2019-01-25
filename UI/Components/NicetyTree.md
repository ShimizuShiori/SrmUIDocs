[TOC]

# NicetyTree

## 1. 用途

用于构建树形控件

## 2. 路径

```
webapp\nicety\src\components\Tree\src\tree.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| data | Array | 树形结构的数据 |
| emptyText | String | 没有数据显示时的文本 |
| renderAfterExpand | Boolean | 在展开后再渲染内容 |
| nodeKey | String | 表示数据中，以哪个属性作为数据标识 |
| checkStrictly | Boolean | 严格选择模式，为 true 时，不会对子节点或父节点进行推断选中 |
| defaultExpandAll | Boolean | 默认时是否展开所有节点 |
| expandOnClickNode | Boolean | 当点击节点时展开子节点 |
| checkOnClickNode | Boolean | 当点击节点时选中节点 |
| checkDescendants | Boolean | 是否选中子节点 |
| autoExpandParent | Boolean | 自动展开父节点 |
| defaultCheckedKeys | String[] | 当 tree 显示时，选中的哪些节点<br/>数据中的每一项是数据中 nodeKey 属性的值 |
| defaultExpandedKeys | String[] | 当 tree 显示时，展开哪些节点 |
| currentNodeKey | String<br/>Number | 当前选中的节点nodeKey，不确定 |
| renderContent | Function | Unknow |
| showCheckbox | Boolean | ... |
| draggable | Boolean | ... |
| allowDrag | Function | Unknow |
| allowDrop | Function | Unknow |
| props | [TreeDataProps](#TreeDataProps) | 数据中与节点控件相同的属性名称 |
| lazy | Boolean | 懒加载 |
| highlightCurrent | Boolean | Unknow |
| load | Function | Unknow |
| filterNodeMethod | Function | Unknow |
| accordion | Boolean | Unknow |
| indent | Number | Unknow |
| iconClass | String | 节点上的图标样式 [不确定] |

### 3.2 api

#### 3.2.1 filter(value)

#### 3.2.2 getNodeKey(node)

#### 3.2.3 getNodePath(data)

#### 3.2.4 getCheckedNodes(leafOnly, includeHalfChecked)

#### 3.2.5 getCheckedKeys(leafOnly)

```typescript
/**
 * 获取选择的节点 nodeKey 值
 * @param leafOnly 是否只返回叶子节点
 * @returns 所有选中的节点的 nodeKey 值的集合
 */
getCheckedKeys(leafOnly: boolean) : string[]{}
```


#### 3.2.6 getCurrentNode()

#### 3.2.7 getCurrentKey()

#### 3.2.8 setCheckedNodes(nodes, leafOnly)
```typescript
/**
 * 设置选中的节点
 * @param keys 需要选中的节点的 nodeKey 所对应的值的集合
 * @param leafOnly 是否只选中叶子节点
 */
setCheckedKeys(keys: string[], leafOnly: boolean) {}
```

#### 3.2.9 setChecked(data, checked, deep)

#### 3.2.10 getHalfCheckedNodes()

#### 3.2.11 getHalfCheckedKeys()

#### 3.2.12 setCurrentNode(node)

#### 3.2.13 setCurrentKey(key)

#### 3.2.14 getNode(data)

#### 3.2.15 remove(data)

#### 3.2.16 append(data, parentNode)

#### 3.2.17 insertBefore(data, refNode)

#### 3.2.18 insertAfter(data, refNode)

#### 3.2.19 handleNodeExpand(nodeData, node, instance)

#### 3.2.20 updateKeyChildren(key, data)

### 3.3 events

#### 3.3.1 node-drag-start

#### 3.3.2 node-drag-leave

#### 3.3.3 node-drag-enter

#### 3.3.4 node-drag-over

#### 3.3.5 node-drag-end

#### 3.3.6 node-drop

#### 3.3.7 node-expand

### 3.4 slots

---

## 附. 其它类型

<b id="TreeDataProps"></b>
### TreeDataProps

```typescript
declare interface TreeDataProps{
    /**
     * 数据中，表示子节点的属性名称
     * 默认值为 children
     */
    children: string;
    /**
     * 数据中，表示用来显示在节点上的文本的属性名称
     * 默认值为 label
     */
    label: string;
    /**
     * 数据中，描述数据是否禁用的属性名称
     * 默认值为 disabled
     */
    disabled: string;
}
```

---

[返回首页][back]

[back]: ../index.md#