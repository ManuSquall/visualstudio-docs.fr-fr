---
title: Fichiers réponse MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315146"
---
# <a name="msbuild-response-files"></a>Fichiers réponse MSBuild

Les fichiers réponse (*.rsp*) sont des fichiers texte qui contiennent des commutateurs de ligne de commande *MSBuild.exe*. Les commutateurs peuvent se trouver chacun sur une ligne distincte ou se trouver tous sur une même ligne. Les lignes de commentaire sont précédées d’un **#** symbole. Le **@** commutateur est utilisé pour passer un autre fichier réponse à *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Le fichier réponse automatique est un fichier *.rsp* spécial utilisé automatiquement par *MSBuild.exe* lors du build d’un projet. Ce fichier (*MSBuild.rsp*) doit se trouver dans le même répertoire que *MSBuild.exe*, sinon il sera introuvable. Vous pouvez modifier ce fichier pour spécifier des commutateurs de ligne de commande par défaut à *MSBuild.exe*. Par exemple, si vous utilisez le même enregistreur d’événements à chaque build de projet, vous pouvez ajouter le commutateur **-logger** à *MSBuild.rsp*. Ainsi, *MSBuild.exe* utilise systématiquement l’enregistreur d’événements.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

Dans les versions 15.6 et ultérieures, MSBuild recherche dans les répertoires parents du projet un fichier nommé *Directory.Build.rsp*.  Cela peut être utile dans un dépôt de code source pour fournir des arguments par défaut aux builds générées à partir de la ligne de commande.  Cela peut également être utile pour spécifier les arguments de ligne de commande des builds hébergées.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)
