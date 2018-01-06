---
title: "Maintenance des recommandations pour isolé des Applications de Shell | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4139512bc63141c24b42d0ef3bd53119f4d1fb0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Les instructions de maintenance pour les Applications de Shell isolé
Lorsque vous distribuez une application de shell isolé Visual Studio, vous devez être en mesure de fournir des mises à jour logicielles pour votre application après son installation. Pour ce faire, vous devez installer votre application à l’aide d’un fichier Microsoft Installer (MSI). Ce type d’installation permet de mises à jour logicielles fournies par Microsoft pour être redistribué par Web téléchargeront et utilisée par vos clients sans intervention personnalisée.  
  
## <a name="servicing-requirements"></a>Besoins en maintenance  
 Vous pouvez vous assurer que votre installation de shell isolé peut autoriser les mises à jour en vous assurant que le programme d’installation répond aux trois critères suivants.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuer à l’aide d’un fichier MSI  
 Vous devez utiliser un fichier MSI afin de redistribuer votre application, car un fichier MSI préserve l’identité du produit et permet de s’assurer que l’application dispose d’un emplacement physique sur l’ordinateur client. Les modules de fusion (fichiers .msm) ne fournissent pas de ces garanties et ne doivent pas être utilisés.  
  
### <a name="accounting-for-custom-actions"></a>Gestion des comptes pour les Actions personnalisées  
 Les actions personnalisées sont des directives d’installation non standard dans un programme d’installation. Actions personnalisées modifier des paramètres tels que les emplacements de fichiers, les paramètres de Registre, les paramètres utilisateur ou autres éléments de l’installation. Actions personnalisées peuvent manipuler des données au moment de l’installation.  
  
 Lorsque vous utilisez des actions personnalisées dans un programme d’installation, vous devez vous assurer que chaque action personnalisée au moment de l’installation doit avoir une action personnalisée correspondante pour annuler l’action lorsque l’utilisateur désinstalle l’application. Si votre programme d’installation échoue pour fournir correspondant désinstaller l’action personnalisée, suppression de votre application reste partiellement installé.  
  
-   Une action personnalisée qui s’appuie sur une version spécifique d’un fichier ou hachage des valeurs échoue lors de la modification de ces versions de mises à jour logicielles ou valeurs de hachage. Dans ce cas l’action personnalisée doit mettre à jour manuellement ces valeurs. Un autre problème se produit si les versions d’un fichier ou le hachage de valeurs sont partagées entre les versions de produit. Évitez cette dépendance chaque fois que possible.  
  
### <a name="accounting-for-shared-files"></a>Gestion des comptes pour les fichiers partagés  
 Fichiers partagés ont le même nom et sont installés par plusieurs produits dans le même emplacement. Ces produits peuvent différer dans la version, référence (SKU Stock Keeping Unit) ou les deux, et les produits peuvent coexister sur un ordinateur donné. Toutefois, les fichiers partagés créer des problèmes de maintenance pour plusieurs raisons :  
  
-   Mise à jour des fichiers partagés peut entraîner des problèmes de compatibilité des applications, car une mise à jour pour une application peut modifier la version d’un fichier utilisé par une autre application n’a pas été mis à jour. Programmes d’installation pour les produits qui partagent des fichiers comptent des références aux fichiers partagés. Par conséquent, la désinstallation d’un produit n’affecte pas les fichiers partagés au-delà de décrémentation du nombre d’instances installées.  
  
-   Le programme d’installation de l’ingénierie QFE (Quick Fix) rétablit les versions des fichiers pour les versions de ces produits prises en charge par le programme d’installation du correctif QFE. Ce processus compose potentiellement une application qui a remis un fichier partagé mis à jour.