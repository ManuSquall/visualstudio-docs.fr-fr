---
title: Instructions de maintenance pour les applications de Shell isolé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159274"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Instructions de maintenance des applications avec Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous distribuez une application Visual Studio isolated Shell, vous devez être en mesure de fournir des mises à jour logicielles pour votre application une fois qu’elle est installée. Pour ce faire, vous devez installer votre application à l’aide d’un fichier Microsoft Installer (MSI). Ce type d’installation permet aux mises à jour logicielles fournies par Microsoft d’être redistribuées par téléchargement sur le Web et consommées par vos clients sans intervention personnalisée.  
  
## <a name="servicing-requirements"></a>Exigences en matière de maintenance  
 Vous pouvez vous assurer que votre installation de Shell isolé peut autoriser les mises à jour en vous assurant que votre programme d’installation remplit les trois critères suivants.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuer à l’aide d’un MSI  
 Vous devez utiliser un MSI pour redistribuer votre application, car un MSI préserve l’identité du produit et s’assure que l’application dispose d’un emplacement physique sur l’ordinateur client. Les modules de fusion (fichiers. msm) ne fournissent pas de telles garanties et ne doivent pas être utilisés.  
  
### <a name="accounting-for-custom-actions"></a>Gestion des actions personnalisées  
 Les actions personnalisées sont des directives d’installation non standard dans un programme d’installation. Les actions personnalisées modifient les paramètres tels que les emplacements de fichiers, les paramètres du Registre, les paramètres utilisateur ou d’autres éléments d’installation. Les actions personnalisées peuvent manipuler des données au moment de l’installation.  
  
 Lorsque vous utilisez des actions personnalisées dans un programme d’installation, vous devez vous assurer que chaque action personnalisée au moment de l’installation doit avoir une action personnalisée correspondante pour annuler l’action lorsque l’utilisateur désinstalle l’application. Si votre programme d’installation ne parvient pas à fournir l’action personnalisée de désinstallation correspondante, la suppression de votre application la laisse partiellement installée.  
  
- Une action personnalisée qui s’appuie sur une version spécifique d’un fichier ou de valeurs de hachage échoue quand les mises à jour logicielles modifient ces versions ou valeurs de hachage. Dans ce cas, votre action personnalisée doit mettre à jour manuellement ces valeurs. Un problème supplémentaire se produit si les versions d’un fichier ou de valeurs de hachage sont partagées entre les versions du produit. Évitez cette dépendance dans la mesure du possible.  
  
### <a name="accounting-for-shared-files"></a>Gestion des fichiers partagés  
 Les fichiers partagés ont le même nom et sont installés dans le même emplacement par plusieurs produits. Ces produits peuvent être différents dans la version, la référence (SKU), ou les deux, et les produits peuvent coexister sur un ordinateur donné. Toutefois, les fichiers partagés créent des problèmes de maintenance pour plusieurs raisons :  
  
- La mise à jour des fichiers partagés peut entraîner des problèmes de compatibilité des applications, car une mise à jour d’une application peut modifier la version d’un fichier utilisé par une deuxième application qui n’a pas été mise à jour. Les programmes d’installation des produits qui partagent des fichiers dénombrent les références aux fichiers partagés. Par conséquent, la désinstallation d’un produit n’affecte pas les fichiers partagés au-delà de la décrémentation du nombre d’instances installées.  
  
- Le programme d’installation du correctif QFE (Quick Fix Engineering) rétablit les versions des fichiers sur les versions des produits que le programme d’installation QFE a servi. Ce processus peut potentiellement interrompre une application qui avait fourni un fichier partagé mis à jour.
