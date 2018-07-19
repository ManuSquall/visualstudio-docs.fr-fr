---
title: 'Comment : rechercher un processus dans la vue processus | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d23199031ce46e57e44a01720493fad4e77c7430
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472476"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Comment : rechercher un processus dans la vue Processus
Vous pouvez rechercher un processus spécifique dans la vue processus à l’aide de sa chaîne de module ou d’ID de processus en tant que critères de recherche. Vous pouvez également spécifier la direction initiale de la recherche. Les champs dans la boîte de dialogue affiche les attributs du processus sélectionné dans l’arborescence du processus.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Pour rechercher un processus dans la vue processus  
  
1.  Fenêtres ainsi que Spy ++ et qu’une [vue processus](../debugger/processes-view.md) fenêtre sont visibles.  
  
2.  À partir de la **recherche** menu, choisissez **rechercher le processus.**  
  
     Le [boîte de dialogue de recherche de processus](../debugger/process-search-dialog-box.md) s’ouvre.  
  
3.  Tapez l’ID de processus ou une chaîne de module comme critère de recherche.  
  
4.  Désactivez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.  
  
    > [!TIP]
    >  Pour rechercher tous les processus détenus par un module, désactivez le **processus** zone, puis tapez le nom du module dans la **Module** boîte. Utilisez ensuite **suivant** pour poursuivre la recherche pour les processus.  
  
5.  Choisissez **des** ou **vers le bas** pour la direction initiale de la recherche.  
  
6.  Cliquez sur **OK**.  
  
 Si un processus de correspondance est trouvé, il est mis en surbrillance dans le **vue processus** fenêtre.