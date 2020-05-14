---
title: Quoi de neuf dans le Studio Visuel 2019 SDK (fr) Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740397"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Nouveautés du SDK Visual Studio 2019

Le Visual Studio SDK a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Avertissement d’extensions rechargeuses rechargeuses synchroneusement

Les utilisateurs verront désormais un avertissement si l’une de leurs extensions installées sont synchronisées autochargées sur le démarrage. Vous pouvez en apprendre davantage sur l’avertissement à [Synchronously autoloaded extensions](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Single, unifié Visual Studio SDK

Vous pouvez maintenant obtenir tous les actifs Visual Studio SDK grâce à un seul paquet NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Améliorations de l’inscription des rédacteurs

Depuis sa création, Visual Studio a pris en charge l’enregistrement des éditeurs personnalisés où un éditeur peut déclarer son affinité pour des extensions spécifiques (par exemple, .xaml et .rc), ou qu’il est adapté à toute extension (. À partir de Visual Studio 2019 version 16.1, nous élargissons le support pour l’inscription de l’éditeur.

### <a name="filenames"></a>Noms de fichiers

En plus d’enregistrer ou au lieu d’enregistrer la prise en charge d’une extension `ProvideEditorFilename` de fichier particulière, un éditeur peut s’inscrire qu’il prend en charge des noms de fichiers spécifiques en appliquant le nouvel attribut à l’emballage de l’éditeur.

Par exemple, un éditeur qui prend en `ProvideEditorExtension` charge tous les fichiers .json appliquerait cet attribut à son package :

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

En commençant par 16.1, si MyEditor ne prend en charge qu’un `ProvideEditorFilename` couple de fichiers .json bien connus, il peut plutôt appliquer ces attributs à son paquet:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContextes

Un éditeur peut enregistrer un ou plusieurs UIContexts qui représentent lorsqu’il est activé. UIContexts sont enregistrés en appliquant `ProvideEditorUIContextAttribute` un ou plusieurs cas de l’emballage qui enregistre l’éditeur.

Si un éditeur a enregistré UIContexts :

- Si au moins un de ses UIContexts enregistrés est actif lorsqu’un fichier avec l’extension donnée est ouvert, l’éditeur est inclus dans la recherche de l’éditeur.
- Si aucun des UIContexts enregistrés n’est actif, l’éditeur n’est pas inclus dans la recherche de l’éditeur.

Si un éditeur n’enregistre pas d’interfaceurs, il est toujours inclus dans la recherche de cette extension.

Par exemple, si un éditeur n’est disponible que lorsqu’un projet C `ProvideEditorUIContext` est ouvert, il peut déclarer cette affinité en appliquant un attribut :

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
