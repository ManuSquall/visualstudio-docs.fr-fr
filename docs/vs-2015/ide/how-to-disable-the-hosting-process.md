---
title: Guide pratique pour désactiver le processus d’hébergement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 813094285557171e9c7f021f597d0d643356b5d4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694411"
---
# <a name="how-to-disable-the-hosting-process"></a>Comment : désactiver le processus d'hébergement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les appels à certaines API peuvent être affectés quand le processus hôte est activé. Dans ces situations, il est nécessaire de désactiver le processus d’hébergement pour retourner les résultats corrects.  
  
### <a name="to-disable-the-hosting-process"></a>Pour désactiver le processus d’hébergement  
  
1. Ouvrez un projet exécutable dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Les projets qui ne produisent pas de fichiers exécutables (par exemple, les projets de bibliothèque de classes ou de service) n’ont pas cette option.  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3. Cliquez sur l’onglet **Déboguer**.  
  
4. Décochez la case **Activer le processus d’hébergement Visual Studio**.  
  
   Quand le processus d’hébergement est désactivé, plusieurs fonctionnalités de débogage sont indisponibles ou subissent une baisse des performances. Pour plus d’informations, consultez [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md).  
  
   En général, quand le processus d’hébergement est désactivé :  
  
- le temps nécessaire pour commencer le débogage des applications [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] augmente ;  
  
- l’évaluation d’une expression au moment du design n’est pas disponible ;  
  
- le débogage de confiance partielle n’est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md)   
 [Processus d’hébergement (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Générations pendant le développement d’une application](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
