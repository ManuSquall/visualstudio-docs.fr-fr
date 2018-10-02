---
title: Fichiers réponse MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 71fdc29db3e2af66c85637648bb0703e7f7d80c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494097"
---
# <a name="msbuild-response-files"></a>Fichiers réponse MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fichiers réponse MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-response-files).  
  
  
Les fichiers réponse (.rsp) sont des fichiers texte qui contiennent des commutateurs de ligne de commande MSBuild.exe. Les commutateurs peuvent se trouver chacun sur une ligne distincte ou se trouver tous sur une même ligne. Les lignes de commentaire sont précédées d’un symbole **#**. Le commutateur **@** est utilisé pour passer un autre fichier réponse à MSBuild.exe.  
  
 Le fichier réponse automatique est un fichier .rsp spécial que MSBuild.exe utilise automatiquement lors de la génération d’un projet. Ce fichier (MSBuild.rsp) doit se trouver dans le même répertoire que MSBuild.exe, sinon il sera introuvable. Vous pouvez modifier ce fichier pour spécifier des commutateurs de ligne de commande par défaut à MSBuild.exe. Par exemple, si vous utilisez le même enregistreur d’événements chaque fois que vous générez un projet, vous pouvez ajouter le commutateur **/logger** au fichier MSBuild.rsp. Ainsi, MSBuild.exe utilise l’enregistreur d’événements chaque fois qu’un projet est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)



