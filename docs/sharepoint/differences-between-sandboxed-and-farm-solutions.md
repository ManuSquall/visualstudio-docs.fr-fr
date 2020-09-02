---
title: Différences entre les solutions sandbox et les solutions de batterie de serveurs | Microsoft Docs
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
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967544"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Différences entre les solutions sandbox et les solutions de batterie de serveurs
  Quand vous compilez une solution SharePoint, elle est déployée sur le serveur SharePoint et un débogueur est attaché pour la déboguer. Le processus utilisé pour déboguer la solution dépend du paramètre de la propriété de la solution bac à sable (sandbox) : solution bac à sable (sandbox) ou solution de batterie de serveurs.

 Pour plus d’informations, consultez [Considérations sur les solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Solutions de batterie de serveurs
 Les solutions de batterie, qui sont hébergées dans le processus de travail IIS (W3WP.exe), exécutent du code qui peut affecter l’ensemble de la batterie. Quand vous déboguez un projet SharePoint dont la propriété de la solution bac à sable (sandbox) a la valeur « solution de batterie », le pool d’applications IIS du système se recycle avant que SharePoint ne rétracte ou ne déploie la fonctionnalité de façon à libérer tous les fichiers verrouillés par le processus de travail IIS. Seul le pool d’applications IIS desservant l’URL du site du projet SharePoint est recyclé.

## <a name="sandboxed-solutions"></a>Solutions bac à sable (sandbox)
 Les solutions bac à sable (sandbox), qui sont hébergées dans le processus de travail de la solution de code utilisateur SharePoint (SPUCWorkerProcess.exe), exécutent du code qui peut uniquement affecter la collection de sites de la solution. Étant donné que les solutions bac à sable (sandbox) ne s’exécutent pas dans le processus de travail IIS, ni le pool d’applications IIS ni le serveur IIS ne doivent redémarrer. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint le débogueur au processus SPUCWorkerProcess que le service SPUserCodeV4 dans SharePoint déclenche et contrôle automatiquement. Il n’est pas nécessaire que le processus SPUCWorkerProcess recycle pour charger la version la plus récente de la solution.

## <a name="either-type-of-solution"></a>L’un ou l’autre type de solution
 Avec l’un ou l’autre type de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache également le débogueur au navigateur pour activer le débogage de script côté client. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le moteur de débogage de script à cet effet. Pour activer le débogage de script, vous devez modifier les paramètres du navigateur par défaut lorsque vous y êtes invité.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache le débogueur uniquement aux processus W3WP ou SPUCWorkerProcess exécutant le site actuel. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache également les moteurs de débogage de flux de travail et COM managés.

## <a name="see-also"></a>Voir aussi
- [Déboguer des solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md)
