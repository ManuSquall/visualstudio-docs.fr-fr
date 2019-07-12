---
title: 'Procédure : Rechercher un processus dans la vue processus | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e39168e36e9540ec8c5e23a9030d996b81c4097c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64799500"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procédure : Rechercher un processus dans la vue Processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rechercher un processus spécifique dans la vue processus à l’aide de sa chaîne d’ID ou un module de processus en tant que critères de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs dans la boîte de dialogue affiche les attributs du processus sélectionné dans l’arborescence de processus.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Pour rechercher un processus dans la vue processus  
  
1. Réorganisez vos fenêtres donc que Spy ++ et qu’une [vue processus](../debugger/processes-view.md) fenêtre sont visibles.  
  
2. À partir de la **recherche** menu, choisissez **rechercher le processus**  
  
    Le [boîte de dialogue de recherche de processus](../debugger/process-search-dialog-box.md) s’ouvre.  
  
3. Tapez l’ID de processus ou une chaîne de module comme critère de recherche.  
  
4. Effacer tous les champs pour lesquels vous ne souhaitez pas spécifier des valeurs.  
  
   > [!TIP]
   > Pour rechercher tous les processus détenus par un module, désactivez le **processus** puis tapez le nom du module dans le **Module** boîte. Utilisez ensuite **suivant** pour poursuivre la recherche pour les processus.  
  
5. Choisissez **des** ou **vers le bas** pour la direction de la recherche initiale.  
  
6. Cliquez sur **OK**.  
  
   Si un processus de correspondance est trouvé, elle est mise en surbrillance dans le **vue processus** fenêtre.
