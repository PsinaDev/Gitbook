# Наглядные примеры реализации делегатов

### Наглядный пример реализации делегатов в Blueprint

1. Создаем Event Dispatcher

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Делегаты в UE называются "Event Dispatcher"</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

2. Называть диспатчеры лучше On\_\[EventName] - передает смысл "когда случилось то-то...", например On Value Changed. Или ED\_MyDispatcherName.
3. На Beginplay с задержкой вызовем наш Event Dispatcher (Call). Это означает, что объект отправил сообщение.

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

4. Теперь уже в другом объекте подпишемся на наш диспатчер

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Assign позволяет сразу создать Event к данному делегату</p></figcaption></figure>



<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Запустив игру с этими объектами на уровне, мы получим такое сообщение</p></figcaption></figure>

### Наглядный пример реализации делегатов в C++

Полезная ссылка: [Продвинутые делегаты в C++ от BenUI](https://benui.ca/unreal/delegates-advanced/)

1. Создаем класс

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

2. В заголовочном файле (.h) объявляем наш делегат

```cpp
// Copyright Protocol:Terminate 2024 - 2025. All rights reserved.
#pragma once

#include "CoreMinimal.h"
#include "GameFramework/Actor.h"
#include "DelegateTestActor.generated.h"

DECLARE_DYNAMIC_MULTICAST_DELEGATE(FOnBeginPlayEvent); // Объявление делегата

UCLASS()
class PROTOCOLTERMINATE_API ADelegateTestActor : public AActor
{
    GENERATED_BODY()

public:
    // Sets default values for this actor's properties
    ADelegateTestActor();

protected:
    // Called when the game starts or when spawned
    virtual void BeginPlay() override;

public:
    // Called every frame
    virtual void Tick(float DeltaTime) override;

    // UPROPERTY делегата. Обратите внимание на метаданные BlueprintAssignable
    UPROPERTY(BlueprintAssignable, Category = "Event")
    FOnBeginPlayEvent OnBeginPlayEvent;
};
```

3. В файле реализации (.cpp) Вызываем наш делегат на BeginPlay

```cpp
// Copyright Protocol:Terminate 2024 - 2025. All rights reserved.

#include "DelegateTestActor.h"

// Sets default values
ADelegateTestActor::ADelegateTestActor()
{
    // Set this actor to call Tick() every frame.  You can turn this off to improve performance if you don't need it.
    PrimaryActorTick.bCanEverTick = true;
}

// Called when the game starts or when spawned
void ADelegateTestActor::BeginPlay()
{
    Super::BeginPlay();

    // Вызов делегата
    OnBeginPlayEvent.Broadcast();
}

// Called every frame
void ADelegateTestActor::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);
}

```

4. Повторяем шаг подписывания на делегат, но уже в BP

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Подписываемся на делегат в C++

пунктик уровня домашнее задание, можете попробовать реализовать ту же логику на C++:

```cpp
void AAnotherActor::BeginPlay()
{
    Super::BeginPlay();
    ADelegateTestActor* DelegateTestActor = FindActor<ADelegateTestActor>(GetWorld());

    if (DelegateTestActor)
    {
        DelegateTestActor->OnBeginPlayEvent.AddDynamic(this, &AAnotherActor::HandleBeginPlayEvent);
    }
}

void AAnotherActor::HandleBeginPlayEvent()
{
    GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("C++ Делегаты рулят!"));
}
```

