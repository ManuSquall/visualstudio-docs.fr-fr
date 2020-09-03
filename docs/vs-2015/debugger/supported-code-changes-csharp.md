---
title: Modifications du code prises en charge (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fc02c11a4ebceea431fc06a1bd1cfdb1063097d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823539"
---
# <a name="supported-code-changes-c"></a>Modifications de code prises en charge (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifier &amp; Continuer gère la plupart des types de modifications du code dans le corps des méthodes. Toutefois, la plupart des modifications en dehors du corps des méthodes et quelques autres à l'intérieur ne peuvent pas s'appliquer pendant le débogage. Pour appliquer ces modifications non prises en charge, vous devez arrêter le débogage et redémarrer avec une version nouvelle du code.  
  
 Les modifications suivantes ne peuvent pas être appliquées à du code C# pendant une session de débogage :  
  
- Modifications à l'instruction en cours ou à toute autre instruction active.  
  
     Les instructions actives incluent toutes les instructions, dans les fonctions figurant dans la pile des appels, qui ont été appelées pour parvenir à l'instruction en cours.  
  
     L'instruction en cours est marquée par un arrière-plan jaune dans la fenêtre source. D'autres instructions actives sont marquées par un arrière-plan grisé et sont en lecture seule. Ces couleurs par défaut peuvent être modifiées dans la boîte de dialogue **Options**.  
  
- Modification de la signature d'un type.  
  
- Ajout d'une méthode anonyme qui capture une variable qui n'a pas été capturée auparavant.  
  
- Ajout, suppression ou modification d'attributs.  
  
- Ajout, suppression ou modification de directives `using`.  
  
- Ajout d'un `foreach`, d'un `using` ou d'un `lock` autour de l'instruction active.  
  
## <a name="unsafe-code"></a>Code unsafe  
 Les modifications apportées à du code unsafe présentent les mêmes restrictions que celles qui portent sur du code sécurisé, avec une restriction supplémentaire : Modifier &amp; Continuer ne prend pas en charge les modifications de code unsafe dans une méthode qui contient l'opérateur `stackalloc`.  
  
## <a name="exceptions"></a>Exceptions  
 Modifier &amp; Continuer prend en charge les modifications apportées aux blocs `catch` et `finally`, à l'exception de l'ajout d'un bloc `catch` ou `finally` autour de l'instruction active, qui n'est pas autorisé.  
  
## <a name="unsupported-scenarios"></a>Scénarios non pris en charge  
 Modifier &amp; Continuer n'est pas disponible dans les scénarios de débogage suivants :  
  
- Débogage du code LINQ dans certaines circonstances. Pour plus d’informations, consultez [Débogage LINQ](../debugger/debugging-linq.md).  
  
  - Capture d'une variable qui n'a pas été capturée auparavant.  

  - Modification du type d’expression de requête (par exemple, sélectionnez a => sélectionnez Nouveau {A = a};)  

  - Suppression d'un `where` qui contient une instruction active.  

  - Suppression d'un `let` qui contient une instruction active.  

  - Suppression d'un `join` qui contient une instruction active.  

  - Suppression d'un `orderby` qui contient une instruction active.  
  
- Débogage en mode mixte (natif/managé).  
  
- Débogage SQL.  
  
- Débogage d’un vidage Dr. Watson.  
  
- Modification du code après une exception non gérée, lorsque l’option «**dérouler la pile des appels sur les exceptions non gérées**» n’est pas sélectionnée.  
  
- Débogage d'une application runtime incorporée.  
  
- Débogage d’une application qui a un **attachement à** au lieu d’exécuter l’application en choisissant **Démarrer** dans le menu **Déboguer** .  
  
- Débogage de code optimisé.  
  
- Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Guide pratique pour utiliser Modifier & Continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
