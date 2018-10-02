---
title: 'Comment : rechercher un processus dans la vue processus | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebb0c6a13db0fdc1a586a78038f759c59f8b110
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507230"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Comment : rechercher un processus dans la vue Processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : rechercher un processus dans la vue processus](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-process-in-processes-view).  
  
Vous pouvez rechercher un processus spécifique dans la vue processus à l’aide de sa chaîne d’ID ou un module de processus en tant que critères de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs dans la boîte de dialogue affiche les attributs du processus sélectionné dans l’arborescence de processus.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Pour rechercher un processus dans la vue processus  
  
1.  Réorganisez vos fenêtres donc que Spy ++ et qu’une [vue processus](../debugger/processes-view.md) fenêtre sont visibles.  
  
2.  À partir de la **recherche** menu, choisissez **rechercher le processus**  
  
     Le [boîte de dialogue de recherche de processus](../debugger/process-search-dialog-box.md) s’ouvre.  
  
3.  Tapez l’ID de processus ou une chaîne de module comme critère de recherche.  
  
4.  Effacer tous les champs pour lesquels vous ne souhaitez pas spécifier des valeurs.  
  
    > [!TIP]
    >  Pour rechercher tous les processus détenus par un module, désactivez le **processus** puis tapez le nom du module dans le **Module** boîte. Utilisez ensuite **suivant** pour poursuivre la recherche pour les processus.  
  
5.  Choisissez **des** ou **vers le bas** pour la direction de la recherche initiale.  
  
6.  Cliquez sur **OK**.  
  
 Si un processus de correspondance est trouvé, elle est mise en surbrillance dans le **vue processus** fenêtre.



