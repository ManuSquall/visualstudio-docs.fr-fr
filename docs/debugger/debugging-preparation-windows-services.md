---
title: Préparer le débogage des services Windows | Microsoft Docs
description: Préparez le débogage des services Windows, qui sont des programmes qui s’exécutent en arrière-plan sous Windows, dans Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fe922106181633f506147decc3b578e7dc6e704
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728211"
---
# <a name="debugging-preparation-windows-services"></a>Préparation du débogage : services Windows
Un service Windows est un programme qui s'exécute en arrière-plan sous Microsoft Windows. Il s'agit par exemple du service Telnet ou du service d'horloge Windows, qui met à jour l'horloge visible de l'ordinateur. Un service Windows ne peut pas être exécuté à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; il doit s'exécuter dans le contexte du Gestionnaire de contrôle des services. Pour plus d’informations, consultez [Création de services Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Débogage des applications de service Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) et [Applications de service Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Comment : déboguer la méthode OnStart](../debugger/how-to-debug-the-onstart-method.md)