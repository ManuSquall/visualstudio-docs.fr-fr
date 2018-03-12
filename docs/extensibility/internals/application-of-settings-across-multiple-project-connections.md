---
title: "Application des paramètres sur plusieurs connexions de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a5d66bf7670d5ba9b6423461bdb5e5482819592f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Application des paramètres sur plusieurs connexions de projet
Un plug-in de contrôle de code source généré à l’aide de la 1.2 de API plug-in de contrôle Source, permet un traitement par lots pour exécuter l’opération de contrôle de code source même entre plusieurs projets ou de plusieurs contextes de connexion. Lots peuvent servir à éliminer redondant, boîtes de dialogue à partir de l’expérience utilisateur par projet.  
  
 Si un utilisateur sélectionne plusieurs éléments qui appartiennent à plusieurs connexions dans un plug-in de contrôle de code source générée à l’aide de la Source de contrôle du plug-in API 1.1, (par exemple, deux les projets Web sur un partage de fichiers différents ordinateurs) et vérifie les, l’utilisateur voit la boîte de dialogue à plusieurs reprises. Cela se produit même si l’utilisateur clique sur le **appliquer à tous les** case à cocher dans la boîte de dialogue, car l’IDE réinitialise son état pour chaque contexte de connexion.  
  
## <a name="new-capability-flag"></a>Nouvel indicateur de fonction  
 `SccBeginBatch`Fonction définit la `SCC_CAP_BATCH` indicateur pour indiquer qu’une opération de traitement par lots est en cours d’exécution  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 Les fonctions suivantes prennent en charge l’opération de traitement par lots :  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 Le `SCCBeginBatch` fonction commence à un groupe d’opérations de contrôle de code source. `SccEndBatch`ferme le groupe. Les groupes ne peuvent pas être imbriqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)