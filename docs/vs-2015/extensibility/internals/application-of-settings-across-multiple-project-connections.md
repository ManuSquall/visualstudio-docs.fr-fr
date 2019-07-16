---
title: Application des paramètres entre plusieurs connexions de projet | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203851"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Application des paramètres entre plusieurs connexions de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un plug-in de contrôle de code source créé à l’aide du 1.2 API de plug-in du contrôle Source, peut utiliser une opération par lot pour exécuter l’opération de contrôle de code source même entre plusieurs projets ou de plusieurs contextes de connexion. Lots peuvent être utilisés pour éliminer redondants, des boîtes de dialogue à partir de l’expérience utilisateur par projet.  
  
 Si un utilisateur sélectionne plusieurs éléments qui appartiennent à plusieurs connexions dans un plug-in de contrôle de code source créée à l’aide de la Source contrôle plug-in API 1.1, (par exemple, deux les projets Web sur le partage de fichiers différentes machines) et les vérifie, l’utilisateur voit la boîte de dialogue à plusieurs reprises. Cela se produit même si l’utilisateur clique sur le **appliquer à tous** case à cocher dans la boîte de dialogue, car l’IDE réinitialise son état pour chaque contexte de connexion.  
  
## <a name="new-capability-flag"></a>Nouvel indicateur de fonctionnalité  
 `SccBeginBatch` Fonction définit la `SCC_CAP_BATCH` indicateur pour indiquer qu’une opération par lot est en cours  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 Les fonctions suivantes prennent en charge l’opération de traitement par lots :  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  Le `SCCBeginBatch` fonction commence à un groupe d’opérations de contrôle de code source. `SccEndBatch` ferme le groupe. Les groupes ne peuvent pas être imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
