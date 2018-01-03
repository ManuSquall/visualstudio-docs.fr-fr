---
title: "Création de stubs de méthodes de tests unitaires avec la commande Créer des tests unitaires | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 539565d5f37c60cfb87b3aa33ab8b82f7fee5015
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="get-started-with-microsoft-intellitest"></a>Bien démarrer avec Microsoft IntelliTest

* Si vous utilisez IntelliTest pour la première fois :
  * visionnez la [vidéo de Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * lisez cette [présentation sur MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * lisez notre [documentation](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)
* Posez vos questions sur [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest)
* Lisez le reste de ce manuel de référence
* Imprimez cette page pour vous y référer rapidement

<a name="important-attributes"></a>
## <a name="important-attributes"></a>Attributs importants

* [PexClass](attribute-glossary.md#pexclass) marque un type contenant **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marque un **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marque un paramètre non Null 

```
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

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>Classes d’assistance statiques importantes

* [PexAssume](static-helper-classes.md#pexassume) évalue les hypothèses (filtrage d’entrée)
* [PexAssert](static-helper-classes.md#pexassert) évalue les assertions
* [PexChoose](static-helper-classes.md#pexchoose) génère de nouveaux choix (entrées supplémentaires)
* [PexObserve](static-helper-classes.md#pexobserve) enregistre les valeurs dynamiques dans les tests générés

```
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

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
