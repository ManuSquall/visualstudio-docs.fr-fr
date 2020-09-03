---
title: Nouveautés du kit de développement logiciel (SDK) Visual Studio 2019 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740397"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Nouveautés du SDK Visual Studio 2019

Le kit de développement logiciel (SDK) Visual Studio propose les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Avertissement sur les extensions chargées de façon synchrone

Les utilisateurs verront désormais un avertissement si l’une des extensions installées est chargée de façon synchrone au démarrage. Vous pouvez en savoir plus sur l’avertissement sur les [extensions chargées de façon synchrone](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Kit de développement logiciel (SDK) unique et unifié pour Visual Studio

Vous pouvez désormais obtenir toutes les ressources du kit de développement logiciel (SDK) Visual Studio par le biais d’un seul package NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Améliorations apportées à l’inscription de l’éditeur

Depuis sa création, Visual Studio a pris en charge l’inscription de l’éditeur personnalisé lorsqu’un éditeur peut déclarer son affinité pour des extensions spécifiques (par exemple,. xaml et. RC) ou s’il convient pour n’importe quelle extension (. *). À compter de Visual Studio 2019 version 16,1, nous élargissons la prise en charge de l’inscription de l’éditeur.

### <a name="filenames"></a>Noms de fichiers

En plus ou au lieu de, l’inscription de la prise en charge d’une extension de fichier spécifique, un éditeur peut inscrire qu’il prend en charge des noms de fichiers spécifiques en appliquant le nouvel `ProvideEditorFilename` attribut au package de l’éditeur.

Par exemple, un éditeur qui prend en charge tous les fichiers. JSON appliquera cet `ProvideEditorExtension` attribut à son package :

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

À partir de 16,1, si MyEditor prend uniquement en charge quelques fichiers. JSON bien connus, il peut appliquer ces `ProvideEditorFilename` attributs à son package :

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Du uicontexts

Un éditeur peut inscrire un ou plusieurs du uicontexts qui représentent le moment où il est activé. Les du uicontexts sont inscrits en appliquant une ou plusieurs instances de `ProvideEditorUIContextAttribute` au package qui inscrit l’éditeur.

Si un éditeur a inscrit des du uicontexts :

- Si au moins l’un de ses du uicontexts inscrits est actif lorsqu’un fichier avec l’extension donnée est ouvert, l’éditeur est inclus dans la recherche de l’éditeur.
- Si aucun des du uicontexts inscrits n’est actif, l’éditeur n’est pas inclus dans la recherche de l’éditeur.

Si un éditeur n’enregistre aucun du uicontexts, il est toujours inclus dans l’éditeur de la recherche pour cette extension.

Par exemple, si un éditeur est disponible uniquement lorsqu’un projet C# est ouvert, il peut déclarer cette affinité en appliquant un `ProvideEditorUIContext` attribut :

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
