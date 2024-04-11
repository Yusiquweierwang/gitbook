## 注意事项

### 改缓存！！

![1710830752388](image/C++forUnreal/1710830752388.png)

（忘记该缓存）

![1710830771396](image/C++forUnreal/1710830771396.png)

### 常见前缀

- F-纯 C++类
- U-继承自 UObject
- A-继承自 Actor
- S-Slate 控件相关类
- H-HitResult 相关类

## 项目结构

![1710829432215](image/C++forUnreal/1710829432215.png)

[1] 存放平台编译代码生成的 dll 文件
[2] 存放配置文件
![1710829489854](image/C++forUnreal/1710829489854.png)

[3] 存放项目资源，如贴图/材质/模型/蓝图
[4] 存放 C++代码源文件

## 游戏架构--GameMode

worldSettins-> GameMode

**架构关系**
![1711253514480](image/C++forUnreal/1711253514480.png)

**AGameMode**
AGameMode 是 AGameModeBase 的子类，拥有一些额外的功能支持多人游戏和旧行为。
所有新建项目默认使用 AGameModeBase。

![1711253705269](image/C++forUnreal/1711253705269.png)

## 文件 介绍

.h
包含函数声明 、类定义、宏定义
.cpp
包含头文件中声明的函数和类的具体实现。

![1710312555038](image/C++forUnreal/1710312555038.png)

![1710312642078](image/C++forUnreal/1710312642078.png)
启动时强制编译

### UE_LOG

用于输出日志的宏
![1710312766710](image/C++forUnreal/1710312766710.png)

### 变量 / 常量

![1710313439092](image/C++forUnreal/1710313439092.png)

### 关键字

![1710313673366](image/C++forUnreal/1710313673366.png)

不能以系统关键字 作为变量名或常量名进行定义。

### 标识符

![1710313781491](image/C++forUnreal/1710313781491.png)

### 数据类型 整形 / 浮点型

![1710313824323](image/C++forUnreal/1710313824323.png)

![1710314135804](image/C++forUnreal/1710314135804.png)

### 字符型

![1710395700569](image/C++forUnreal/1710395700569.png)

### 字符串型

![1710395731705](image/C++forUnreal/1710395731705.png)

## 运算符

![1710396430174](image/C++forUnreal/1710396430174.png)

## TArray

C++中的动态数组，所有元素为相同类型。

![1710834771508](image/C++forUnreal/1710834771508.png)
蓝图中

C++中

![1711254362360](image/C++forUnreal/1711254362360.png)

![1711254437249](image/C++forUnreal/1711254437249.png)

## TMap

## TSet

![1710836962482](image/C++forUnreal/1710836962482.png)
合并元素

![1710837052080](image/C++forUnreal/1710837052080.png)

![1710837988995](image/C++forUnreal/1710837988995.png)

## 结构体-USTRUCT

注：定义结构体名称前要加 F 前缀，否则编译报错。

```cpp
USTRUCT(BlueprintType)
struct FMyCustomStruct
{
	GENERATED_USTRUCT_BODY()

	UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyStructType")
	FString ID;
	UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyStructType")
	FString Name;
	UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyStructType")
	int32 Age;
	UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyStructType")
	float Height;
	UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyStructType")
	bool IsMan;
};
```

声明结构体：

```cpp
UPROPERTY(EditAnywhere , BluePrintReadWrite,Category = "MyCustomStruct")
FMyCustomStruct MyCustomStruct;
```

之后可以在蓝图中看到：
![1711266079545](image/C++forUnreal/1711266079545.png)

### 利用结构体创建一个数据表格

## UE - UObject / UGameInstance 实例化

## 提升代码编译速度

![1710314011526](image/C++forUnreal/1710314011526.png)

## Object / Actor / Pawn / Character 类的继承结构

![1711377862264](image/C++forUnreal/1711377862264.png)

这些基本类又派生出了很多子类，比如：

![1711377900433](image/C++forUnreal/1711377900433.png)

## Actor

AActor 是所有 Actor 的基类。
**总结**
![1711874068425](image/C++forUnreal/1711874068425.png)

### 为 Actor 添加组件

![1711269697030](image/C++forUnreal/1711269697030.png)

![1711269737232](image/C++forUnreal/1711269737232.png)

## Component

![1711797728510](image/C++forUnreal/1711797728510.png)

SceneComponent 提供两个功能：

- Transform
- SceneComponent 的互相嵌套

![1711797803013](image/C++forUnreal/1711797803013.png)

### Actor & Component

`TSet<UActorComponent*> OwnedComponents` 保存着这个 Actor 所拥有的所有 Component.
一般其中会有一个 `SceneComponent`作为 `RootComponent`。

`TArray<UActorComponent*> InstanceComponents`中保存着实例化的 Components。

一个 Actor 若想被放进 level 里，必须实例化 USceneComponent\* RootComponent。

**Actor 中的 SceneComponent 设计哲学**
![1711797912485](image/C++forUnreal/1711797912485.png)

关键在于怎样划分要操作的实体的粒度。

![1711797972676](image/C++forUnreal/1711797972676.png)

### ChildActorComponent

## Pawn

代表游戏世界中的可控制角色或物体的基类。
继承自 Actor 类。

可通过 Controller 控制 Pawn 的移动和行为。

![1711809753364](image/C++forUnreal/1711809753364.png)

![1711809876217](image/C++forUnreal/1711809876217.png)

### DefaultPawn / SpectatorPawn / Character

![1711810038692](image/C++forUnreal/1711810038692.png)

### AController

![1711812089686](image/C++forUnreal/1711812089686.png)

### Controller 和 Pawn 必须 1：1 吗？

![1711814127494](image/C++forUnreal/1711814127494.png)

### Controller 的位置和移动的意义

Controller 本身有位置信息，就可以利用该信息更好的控制 Pawn 的位置和移动。

![1711814751460](image/C++forUnreal/1711814751460.png)

### 哪些逻辑放在 Pawn，哪些逻辑放在 Controller?

![1711815274134](image/C++forUnreal/1711815274134.png)

![1711815460629](image/C++forUnreal/1711815460629.png)

![1711870209661](image/C++forUnreal/1711870209661.png)

### APlayState

![1711815984210](image/C++forUnreal/1711815984210.png)

### **APlayController**

在多人联机对战中。
PlayController 不仅能控制本地 Pawn，还能控制远程 Pawn（实际是通过 Server 上 PlayController 控制 Server 上的 Pawn，然后再复制到远程机器上的 Pawn 实现）。
![1711870580898](image/C++forUnreal/1711870580898.png)

### 哪些逻辑放在 PlayController 中？

![1711870938883](image/C++forUnreal/1711870938883.png)

### **AAIController**

![1711871573610](image/C++forUnreal/1711871573610.png)

区别：
与 PlayController 比，缺少了 Camera/Input/Uplay 关联/HUD 显示/voice/Level 切换接口。

增加了一些 AI 需要的组件：

- Navigation，用于智能根据导航寻路，如 MoveTo 接口。再移动时，因为少了玩家控制的来转向，所以多了 SetFocus 来控制当前的 Pawn 视角朝向哪个位置。
- AI 组件，运行启动行为树，使用黑板数据，探索周围环境，以后如果有别的 AI 算法方法实现成组件，也应该再本组件内组合启动。
- Task 系统，让 AI 完成一些任务

### CapsuleComponent 胶囊体

是虚幻引擎中的一种碰撞组件。它是一种用于代表角色或物体碰撞形状的组件，通常用于处理角色的碰撞检测以及角色间的交互。CapsuleComponent 的形状类似于一个胶囊，即上下两个半球连接的形状。通过调整 CapsuleComponent 的高度和半径，可以根据角色或物体的尺寸来定义其碰撞区域。CapsuleComponent 还可以设置碰撞响应和碰撞消息的处理方式，以便在碰撞发生时执行相应的操作。
![1711810252915](image/C++forUnreal/1711810252915.png)

## UPlayer

AActor 必须在 world 中才能存在，而 Player 可以在游玩过程中 LevelWorld 不停切换，玩家模式不变。

![1711953460326](image/C++forUnreal/1711953460326.png)

### ULocalPlayer

## 重写 beginplay() / tick() / endPlay()

.h 中
![1710835633044](image/C++forUnreal/1710835633044.png)
.cpp 中
![1710835664442](image/C++forUnreal/1710835664442.png)

## UPROPERTY

UPROPERTY()宏用来修饰 C++中的变量。

使用 UPROPERTY 说明符赋予属性特性。

- visible

![1710844757165](image/C++forUnreal/1710844757165.png)

```cpp
public:
	//class defaults可见不可写入,其他地方不可见,不可读写
	UPROPERTY(VisibleDefaultsOnly, Category ="TestVisible|VisibleDefaultsOnly")
	int32 VisibleDefaultsValue;
```

**Category**是分类的意思，可以在蓝图调用的时候去显现出来将想要的东西挂载到此分类下面。

- edit
- read / write

![1710844106069](image/C++forUnreal/1710844106069.png)

## UFUNCTION

**设置变量和函数到蓝图中**：
![Alt text](https://img-blog.csdnimg.cn/bafb61db47b04aef89c4ee284140ed47.png)
![1711378434573](image/C++forUnreal/1711378434573.png)
运行后，写的数据就可以到 UE 的蓝图类中使用：
![1711378465395](image/C++forUnreal/1711378465395.png)

## 静态/动态加载类和资源

### 静态加载资源

静态加载资源：
复制静态资源引用
![1711273210799](image/C++forUnreal/1711273210799.png)

无法解析符号？
![1711274407831](image/TODO/1711274407831.png)

### 静态加载类

```cpp
UPROPERTY(VisibleAnywhere ,BlueprintReadOnly, Category = "MyClass");
TSubclassOf<AActor> MyActorClass;

```

**加载静态类时，在引用资源类的末尾需要 加上\_C，否则编译时会报错。**

```cpp
	// 静态加载类  加载静态类时，在引用资源类的末尾需要加上 _C，否则编译时会报错
	static ConstructorHelpers::FClassFinder<AActor> TempActorClass(TEXT("/Script/Engine.Blueprint'/Game/StarterContent/Blueprints/Blueprint_CeilingLight.Blueprint_CeilingLight_C'"));
	MyActorClass = TempActorClass.Class;
	UE_LOG(LogTemp, Warning, TEXT("MyActorClass is %s"), *MyActorClass->GetName());

```

### 动态加载类

## UI 编辑

创建 UI 控件蓝图：
内容浏览器右键--用户界面--控件蓝图 widget blueprint

## 反射机制

反射数据描述了类在运行时的内容。

包括
类名
类中数据成员
每个数据成员类型
每个成员位于对象内存映像的偏移 offset
类的所有成员函数信息。

例如：
创建了一个 Actor 类，有一个 Actor 类型指针去指向此 Actor 类，若指针被销毁了，则此 Actor 类 UE 系统会判断为垃圾，参与反射和垃圾回收系统后，UE 会在适当时机销毁此 Actor。

- 使用宏进行标识，UE 的 UHT 系统会帮忙进行垃圾回收。

![1711378063602](image/C++forUnreal/1711378063602.png)

## 自定义 C++类派生蓝图类

## 一些 function 用法

### Format Text

![1710859827592](image/C++forUnreal/1710859827592.png)

### 函数和纯函数

pure function calls （纯函数调用）不会直接影响世界或世界中 的对象。

**这些函数一般执行类似于这样的事情: 输出一个属性值、数学运算操作(比如两个值间的加减乘除等)， 所产生的结果不会对任何事物造成影响。 只有将该结果进行赋值或使用该结果，才能对世界产生影响。**

## 坐标系统

在源码实现中，在场景中可移动的【Actor】都拥有【USceneComponent 组件】，【世界坐标】的信息是存储于【USceneComponent 组件】中的一个【FTransform】类型的名为【ComponentToWorld】的三维变换矩阵中，除此之外，该三维矩阵也保存了场景对象旋转与缩放的信息：

![Alt text](https://pic2.zhimg.com/80/v2-1e2e1b093223de16519969611a745d15_720w.webp)

### 相对坐标

用 `FVector`类型成员变量存储于 `SceneComponent`组件的 RelativeLocation 中。

## Level

![1711798697757](image/C++forUnreal/1711798697757.png)

**Level 层次的控制**：

![1711882997359](image/C++forUnreal/1711882997359.png)

**ALevelScriptActor**
允许在关卡里编写脚本。

**AInfo**
记录本 level 各种规则和属性

### AWorldSettings

与**AInfo**直接相关

AWorldSettings 要放进 Actors[0]的位置。

## World

- 可以使用 SubLevel 的方式拼装

![1711799463013](image/C++forUnreal/1711799463013.png)

- 也可以使用 WorldComposition 的方式自动把项目中的所有 Level 组合起来，设置摆放位置。
  ![1711799569364](image/C++forUnreal/1711799569364.png)

UE 中每个 World 支持一个 PersistentLevel 和多个其他 Level。

## WorldContext

UE 中 World 不只一种类型，如编辑器本身也是一种 World，里面显示的游戏场景也是一个 World。
点播放时，引擎可以生成新的类型 World 供我们测试。

以下是一些世界类型：
![1711799970238](image/C++forUnreal/1711799970238.png)

管理和跟踪这些 World 的工具：WorldContext

![1711800016151](image/C++forUnreal/1711800016151.png)

WorldContext 既负责 World 之间切换的上下文，也负责 Level 之间切换的操作信息。

### GameInstance

![1711800382468](image/C++forUnreal/1711800382468.png)

GameInstance 中会保存着当前 WorldContext 和其他整个游戏的信息。

独立于 Level 的逻辑或数据要在 GameInstance 中存储。

## GameMode（理解为 WorldController）、

一个 World 的 Controller 不需要展示渲染，因为直接从 AInfo 派生。
笼统来说，一个 World 就是一个 Game，把玩法叫做 Mode。

![1711874832368](image/C++forUnreal/1711874832368.png)

GameMode 主要功能：

- **Class 登记**
  登记游戏里基本需要的类型信息，需要的时候通过 UClass 的反射自动 Spawn 出响应的对象添加到关卡中。
- **游戏内实体的 Spawn**
  游戏加载释放过程中涉及到的实体的产生，包括玩家 Pawn / PlayerController / AIController
  最主要的 SpawnDefaultPawnFor、SpawnPlayerController、ShouldSpawnAtStartSpot 这一系列函数都是在接管玩家实体的生成和释放，玩家进入该游戏的过程叫做 Login（和服务器统一），也控制进来后在什么位置，等等这些实体管理的工作。GameMode 也控制着本场游戏支持的玩家、旁观者和 AI 实体的数目。
- **游戏的进度**
- **Level 的切换**
- **多人游戏的步调同步**

### 多个 Level 配置不同的 GameMode 时采用的是哪一个 GameMode?

![1711875746397](image/C++forUnreal/1711875746397.png)

### 哪些逻辑应该写在 GameMode 中？哪些应该写在 LevelBluePrint 中？

![1711875827787](image/C++forUnreal/1711875827787.png)

### GameState - 保存游戏状态

APlayerState 用来保存玩家的游戏数据集，对于一场游戏，需要一个 State 保存当前游戏的状态数据，如任务数据等。

![1711882932366](image/C++forUnreal/1711882932366.png)

## Engine

![1711800567623](image/C++forUnreal/1711800567623.png)
