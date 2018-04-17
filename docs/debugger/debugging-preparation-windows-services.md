---
title: 'Préparation du débogage : Services Windows | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 488e634ae77b428fdf426680cd17e72b8a462dae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-preparation-windows-services"></a>Préparation du débogage : services Windows
Un service Windows est un programme qui s'exécute en arrière-plan sous Microsoft Windows. Il s'agit par exemple du service Telnet ou du service d'horloge Windows, qui met à jour l'horloge visible de l'ordinateur. Un service Windows ne peut pas être exécuté à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; il doit s'exécuter dans le contexte du Gestionnaire de contrôle des services. Pour plus d’informations, consultez [création de Services Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [débogage des Applications de Service Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications), et [Applications de Service Windows](/dotnet/framework/windows-services/index).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Guide pratique pour déboguer la méthode OnStart](../debugger/how-to-debug-the-onstart-method.md)