---
title: "Guide pratique pour désactiver le processus d’hébergement | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-disable-the-hosting-process"></a>Comment : désactiver le processus d'hébergement
Les appels à certaines API peuvent être affectés quand le processus hôte est activé. Dans ces situations, il est nécessaire de désactiver le processus d’hébergement pour retourner les résultats corrects.  
  
### <a name="to-disable-the-hosting-process"></a>Pour désactiver le processus d’hébergement  
  
1.  Ouvrez un projet exécutable dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les projets qui ne produisent pas de fichiers exécutables (par exemple, les projets de bibliothèque de classes ou de service) n’ont pas cette option.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3.  Cliquez sur l’onglet **Déboguer**.  
  
4.  Décochez la case **Activer le processus d’hébergement Visual Studio**.  
  
 Quand le processus d’hébergement est désactivé, plusieurs fonctionnalités de débogage sont indisponibles ou subissent une baisse des performances. Pour plus d’informations, consultez [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md).  
  
 En général, quand le processus d’hébergement est désactivé :  
  
-   le temps nécessaire pour commencer le débogage des applications [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] augmente ;  
  
-   l’évaluation d’une expression au moment du design n’est pas disponible ;  
  
-   le débogage de confiance partielle n’est pas disponible.  
  
## <a name="see-also"></a>Voir aussi

[Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md)   
[Processus d’hébergement (vshost.exe)](../ide/hosting-process-vshost-exe.md)