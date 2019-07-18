---
title: Fichiers réponse MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189376"
---
# <a name="msbuild-response-files"></a>Fichiers réponse MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les fichiers réponse (.rsp) sont des fichiers texte qui contiennent des commutateurs de ligne de commande MSBuild.exe. Les commutateurs peuvent se trouver chacun sur une ligne distincte ou se trouver tous sur une même ligne. Les lignes de commentaire sont précédées d’un symbole **#** . Le commutateur **@** est utilisé pour passer un autre fichier réponse à MSBuild.exe.  
  
 Le fichier réponse automatique est un fichier .rsp spécial que MSBuild.exe utilise automatiquement lors de la génération d’un projet. Ce fichier (MSBuild.rsp) doit se trouver dans le même répertoire que MSBuild.exe, sinon il sera introuvable. Vous pouvez modifier ce fichier pour spécifier des commutateurs de ligne de commande par défaut à MSBuild.exe. Par exemple, si vous utilisez le même enregistreur d’événements chaque fois que vous générez un projet, vous pouvez ajouter le commutateur **/logger** au fichier MSBuild.rsp. Ainsi, MSBuild.exe utilise l’enregistreur d’événements chaque fois qu’un projet est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)
