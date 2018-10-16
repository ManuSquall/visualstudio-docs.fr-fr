---
title: Fichiers réponse MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 09271f90eb0b065df6c6f28bc318509d7141a252
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242292"
---
# <a name="msbuild-response-files"></a>Fichiers réponse MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Les fichiers réponse (.rsp) sont des fichiers texte qui contiennent des commutateurs de ligne de commande MSBuild.exe. Les commutateurs peuvent se trouver chacun sur une ligne distincte ou se trouver tous sur une même ligne. Les lignes de commentaire sont précédées d’un symbole **#**. Le commutateur **@** est utilisé pour passer un autre fichier réponse à MSBuild.exe.  
  
 Le fichier réponse automatique est un fichier .rsp spécial que MSBuild.exe utilise automatiquement lors de la génération d’un projet. Ce fichier (MSBuild.rsp) doit se trouver dans le même répertoire que MSBuild.exe, sinon il sera introuvable. Vous pouvez modifier ce fichier pour spécifier des commutateurs de ligne de commande par défaut à MSBuild.exe. Par exemple, si vous utilisez le même enregistreur d’événements chaque fois que vous générez un projet, vous pouvez ajouter le commutateur **/logger** au fichier MSBuild.rsp. Ainsi, MSBuild.exe utilise l’enregistreur d’événements chaque fois qu’un projet est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)



