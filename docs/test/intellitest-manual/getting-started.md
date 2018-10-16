---
title: Introduction à IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 37246d3dc612a44057c21f41145414f60bac0860
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46135471"
---
# <a name="get-started-with-microsoft-intellitest"></a>Bien démarrer avec Microsoft IntelliTest

* Si vous utilisez IntelliTest pour la première fois :
  * visionnez la [vidéo de Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * lisez cette [présentation sur MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * lisez notre [documentation](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Posez vos questions sur [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest)
* Lisez le reste de ce manuel de référence
* Imprimez cette page pour vous y référer rapidement

## <a name="important-attributes"></a>Attributs importants

* [PexClass](attribute-glossary.md#pexclass) marque un type contenant **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marque un **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marque un paramètre non Null

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) lie un projet de test à un projet
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) spécifie un assembly à instrumenter

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Classes d’assistance statiques importantes

* [PexAssume](static-helper-classes.md#pexassume) évalue les hypothèses (filtrage d’entrée)
* [PexAssert](static-helper-classes.md#pexassert) évalue les assertions
* [PexChoose](static-helper-classes.md#pexchoose) génère de nouveaux choix (entrées supplémentaires)
* [PexObserve](static-helper-classes.md#pexobserve) enregistre les valeurs dynamiques dans les tests générés

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).
