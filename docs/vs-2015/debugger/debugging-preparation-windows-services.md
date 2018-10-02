---
title: 'Préparation du débogage : Services Windows | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b189c1533e112c023ce2da24ed61fe228c09fda
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494563"
---
# <a name="debugging-preparation-windows-services"></a>Préparation du débogage : services Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [préparation du débogage : Services de Windows](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-windows-services).  
  
Un service Windows est un programme qui s'exécute en arrière-plan sous Microsoft Windows. Il s'agit par exemple du service Telnet ou du service d'horloge Windows, qui met à jour l'horloge visible de l'ordinateur. Un service Windows ne peut pas être exécuté à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; il doit s'exécuter dans le contexte du Gestionnaire de contrôle des services. Pour plus d’informations, consultez [création de Services Windows](http://msdn.microsoft.com/library/0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff), [débogage des Applications de Service Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2), et [Windows Service Applications](http://msdn.microsoft.com/library/ba72d648-9553-4849-b829-069ad5ea014b).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Guide pratique pour déboguer la méthode OnStart](../debugger/how-to-debug-the-onstart-method.md)



