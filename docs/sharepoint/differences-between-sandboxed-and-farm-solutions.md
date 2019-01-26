---
title: Différences entre le bac à sable et les Solutions de batterie | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49dcd021e3f04d78af9d0ff50e7001dedcc73297
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867856"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Différences entre le bac à sable et les solutions de batterie
  Lorsque vous compilez une solution SharePoint, il déploie sur le serveur SharePoint et un débogueur est attaché pour le déboguer. Le processus utilisé pour déboguer la solution varie selon le paramètre de la propriété Solution bac à sable : solution bac à sable ou la solution de batterie de serveurs.  
  
 Pour plus d’informations, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Solutions de batterie de serveurs
 Les solutions de batterie de serveurs, qui sont hébergées dans le processus de travail IIS (W3WP.exe), exécutent le code qui peut affecter la batterie entière. Lorsque vous déboguez un projet SharePoint dont la propriété Solution bac à sable est définie à « solution de batterie de serveurs », le pool d’applications IIS du système est recyclé avant que SharePoint retire ou déploie la fonctionnalité afin de libérer tous les fichiers verrouillés par le processus de travail IIS. Uniquement le pool d’applications IIS desservant les URL du site du projet SharePoint est recyclé.  
  
## <a name="sandboxed-solutions"></a>Solutions bac à sable
 Les solutions sandbox, qui sont hébergées dans le processus de travail de la solution code d’utilisateur SharePoint (SPUCWorkerProcess.exe), exécutent le code qui peut affecter uniquement la collection de sites de la solution. Étant donné que les solutions bac à sable ne s’exécutent pas dans le processus de travail IIS, le pool d’applications IIS, ni le serveur IIS doit redémarrer. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache le débogueur au processus SPUCWorkerProcess que le service SPUserCodeV4 dans SharePoint déclenche automatiquement les contrôles. Il n’est pas nécessaire pour le processus SPUCWorkerProcess recyclage pour charger la dernière version de la solution.  
  
## <a name="either-type-of-solution"></a>Ces deux types de solution
 Avec un type de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] également attache le débogueur au navigateur pour activer le débogage de script côté client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le moteur à cet effet de débogage de script. Pour activer le débogage de script, vous devez modifier les paramètres du navigateur par défaut lorsque vous y êtes invité.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache le débogueur uniquement aux processus W3WP ou SPUCWorkerProcess exécutant le site actuel. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache également les moteurs de débogage de workflow et COM Plus géré.  
  
## <a name="see-also"></a>Voir aussi
 [Déboguer des solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md)  
