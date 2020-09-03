---
title: Application de paramètres sur plusieurs connexions de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203851"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Application des paramètres entre plusieurs connexions de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un plug-in de contrôle de code source créé à l’aide de l’API de plug-in de contrôle de code source 1,2 peut utiliser une opération de traitement par lots pour exécuter la même opération de contrôle de code source sur plusieurs projets ou plusieurs contextes de connexion. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes et par projet de l’expérience utilisateur.  
  
 Si un utilisateur sélectionne plusieurs éléments appartenant à plusieurs connexions dans un plug-in de contrôle de code source créé à l’aide de l’API de plug-in de contrôle de code source 1,1, (par exemple, deux projets Web sur différents ordinateurs de partage de fichiers) et les extrait, l’utilisateur voit la même boîte de dialogue de façon répétée. Cela se produit même si l’utilisateur clique sur la case à cocher **appliquer à tous** dans la boîte de dialogue, car l’environnement de développement intégré (IDE) réinitialise son état pour chaque contexte de connexion.  
  
## <a name="new-capability-flag"></a>Nouvel indicateur de fonctionnalité  
 `SccBeginBatch` La fonction définit l' `SCC_CAP_BATCH` indicateur pour indiquer qu’une opération de traitement par lot est en cours  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 Les nouvelles fonctions suivantes prennent en charge l’opération de traitement par lots :  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  La `SCCBeginBatch` fonction démarre un groupe d’opérations de contrôle de code source. `SccEndBatch` ferme le groupe. Les groupes ne peuvent pas être imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
