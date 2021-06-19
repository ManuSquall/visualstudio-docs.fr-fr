---
title: Traitement des modèles de texte à l'aide d'un hôte personnalisé
description: Découvrez que le processus de transformation de modèle de texte utilise un fichier de modèle de texte comme entrée et produit un fichier texte comme sortie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a301df6edaf8558ade5c8a297f233b58de6d8f4e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390930"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Traiter des modèles de texte à l’aide d’un hôte personnalisé

Le processus de *transformation de modèle de texte* utilise un fichier de modèle de *texte* comme entrée et produit un fichier texte comme sortie. Vous pouvez appeler le moteur de transformation de texte à partir d’une extension Visual Studio ou d’une application autonome s’exécutant sur un ordinateur sur lequel Visual Studio est installé. Toutefois, vous devez fournir un *hôte de création de modèles de texte*. Cette classe connecte le modèle à l'environnement, recherchant des ressources telles que les assemblys et les fichiers Include, et traitant les messages d'erreur et de sortie.

> [!TIP]
> Si vous écrivez un package ou une extension qui s’exécutera dans Visual Studio, envisagez d’utiliser le service de création de modèles de texte au lieu d’écrire votre propre hôte. Pour plus d’informations, consultez [appel de la transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Il est préférable de ne pas utiliser les transformations de modèle de texte dans les applications serveur. Il est déconseillé de les employer, sauf dans un thread unique. En effet, le moteur de création de modèles de texte réutilise un AppDomain unique pour traduire, compiler et exécuter des modèles. Le code traduit n'a pas été conçu pour être thread-safe. Le moteur est conçu pour traiter les fichiers en série, comme dans un projet Visual Studio au moment du Design.
>
> Pour les applications au moment de l’exécution, envisagez d’utiliser des modèles de texte prétraités : consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Si votre application utilise un ensemble de modèles fixés au moment de la compilation, il est plus facile d'employer des modèles de texte prétraités. Vous pouvez également utiliser cette approche si votre application s’exécute sur un ordinateur sur lequel Visual Studio n’est pas installé. Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Exécuter un modèle de texte dans votre application

Pour exécuter un modèle de texte, vous pouvez appeler la méthode ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Votre application doit rechercher et fournir le modèle, de même que traiter la sortie.

 Dans le `host` paramètre, vous devez fournir une classe qui implémente [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Celle-ci est rappelée par le moteur.

 L'hôte doit être en mesure de consigner les erreurs, de résoudre les références à l'assembly et aux fichiers Include, de fournir un domaine d'application dans lequel le modèle peut s'exécuter et d'appeler le processeur approprié pour chaque directive.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> est défini dans **Microsoft. VisualStudio. TextTemplating. \*.0.dll**, et [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) est défini dans **Microsoft. visualstudio. TextTemplating. interfaces. \*.0.dll**.

## <a name="in-this-section"></a>Dans cette section
 [Procédure pas à pas : création d’un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md) Montre comment créer un hôte de modèle de texte personnalisé qui rend la fonctionnalité de modèle de texte disponible en dehors de Visual Studio.

## <a name="reference"></a>Informations de référence
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sections connexes

- [Le processus de transformation de modèle de texte](../modeling/the-text-template-transformation-process.md) décrit le fonctionnement de la transformation de texte et les parties que vous pouvez personnaliser.
- [Création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md) fournit une vue d’ensemble des processeurs de directive de modèle de texte.
