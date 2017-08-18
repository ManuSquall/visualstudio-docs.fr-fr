---
title: "Propriétés d’erreurs spéciales des méthodes asynchrones Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Propriétés d’erreurs spéciales des méthodes asynchrones Windows Runtime
Il peut être difficile de déboguer les méthodes Windows Runtime asynchrones dans JavaScript, car l’erreur peut être levée dans les profondeurs de la pile des appels. L’objet JavaScript `Error` a des propriétés supplémentaires qui s’affichent uniquement quand l’erreur est levée à partir d’une méthode Windows Runtime asynchrone lorsque l’application s’exécute en mode débogage.  
  
## <a name="special-error-properties"></a>Propriétés d’erreurs spéciales  
 Un objet d’erreur qui résulte de l’échec d’une opération Windows Runtime asynchrone en mode débogage a les propriétés spéciales suivantes :  
  
-   `asyncOpSource` (objet) obtient des informations sur l’emplacement d’origine où l’appel ayant généré une erreur a été effectué. La propriété `asyncOpSource.originatingCall` (chaîne) affiche l’emplacement dans le code de l’utilisateur à l’origine de l’opération asynchrone.  
  
-   asyncOpType (chaîne) obtient le nom du type d’opération asynchrone ayant levé l’erreur.  
  
 Pour plus d’informations sur les erreurs avec des opérations asynchrones, consultez :  
  
-   [Guide pratique pour traiter les erreurs liées aux promesses](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Dépannage des erreurs Windows Runtime](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)
