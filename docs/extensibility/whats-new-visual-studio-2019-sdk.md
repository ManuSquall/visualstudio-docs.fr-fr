---
title: Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2019 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30ab0004a492316ff9cbe11016e24b1a28dadf16
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444890"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Nouveautés du SDK Visual Studio 2019

Le SDK Visual Studio a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Mode synchrone les extensions chargées automatiquement avertissement

Les utilisateurs verront désormais un avertissement si une de leurs extensions installées est synchrone chargées automatiquement au démarrage. Plus d’informations sur l’avertissement à [synchrone des extensions chargées automatiquement](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Unifiée du SDK Visual Studio

Vous pouvez désormais obtenir toutes les ressources du Kit de développement logiciel Visual Studio via un seul package NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Améliorations de l’inscription de l’éditeur

Depuis sa création, Visual Studio a pris en charge l’inscription d’éditeur personnalisé où un éditeur peut déclarer ses affinité pour les extensions spécifiques (par exemple, un .xaml et .rc), ou qu’il est adapté à n’importe quelle extension (. *). À partir de Visual Studio 2019 version 16.1, nous élargir la prise en charge pour l’inscription de l’éditeur.

### <a name="filenames"></a>Noms de fichiers

En plus, ou plutôt que l’inscription de la prise en charge pour une extension de fichier particulier, un éditeur peut inscrire qu’il prend en charge les noms de fichiers spécifiques en appliquant la nouvelle `ProvideEditorFilename` au package de l’éditeur d’attribut.

Par exemple, un éditeur qui prend en charge tous les fichiers .json s’appliquera ce `ProvideEditorExtension` attribut son package :

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

À partir de 16,1, si MyEditor prend uniquement en charge les deux fichiers .json bien connu, il peut à la place appliquer ces `ProvideEditorFilename` des attributs à son package :

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un éditeur peut inscrire une ou plusieurs UIContexts qui représentent les lorsqu’elle est activée. UIContexts sont enregistré en appliquant une ou plusieurs instances de `ProvideEditorUIContextAttribute` au package qui inscrit l’éditeur.

Si un éditeur a UIContexts inscrit :

- Si au moins un de ses UIContexts inscrit est actif quand un fichier avec l’extension donnée est ouvert, l’éditeur est inclus dans la recherche de l’éditeur.
- Si aucune de la UIContexts inscrit est active, l’éditeur n’est pas inclus dans la recherche de l’éditeur.

Si un éditeur n’enregistre pas les UIContexts, il est toujours inclus dans la recherche de l’éditeur pour cette extension.

Par exemple, si un éditeur est disponible uniquement lorsque un C# projet est ouvert, il peut déclarer cette affinité en appliquant un `ProvideEditorUIContext` attribut :

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
