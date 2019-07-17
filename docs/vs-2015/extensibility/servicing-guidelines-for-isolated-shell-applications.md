---
title: Maintenance des instructions pour des Applications de Shell isolées | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159274"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Instructions de maintenance des applications avec Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous distribuez une application de shell isolé Visual Studio, vous devez être en mesure de fournir des mises à jour logicielles pour votre application après son installation. Pour ce faire, vous devez installer votre application à l’aide d’un fichier Microsoft Installer (MSI). Ce type d’installation permet des mises à jour logicielles fournies par Microsoft pour être redistribué par Web téléchargent et consommée par vos clients sans intervention personnalisée.  
  
## <a name="servicing-requirements"></a>Besoins en maintenance  
 Vous pouvez vous assurer que votre installation de shell isolé peut autoriser des mises à jour en vous assurant que votre programme d’installation répond à trois critères suivants.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuer à l’aide d’un fichier MSI  
 Vous devez utiliser un fichier MSI pour redistribuer de votre application, car un fichier MSI préserve l’identité du produit et permet de s’assurer que l’application a un emplacement physique sur l’ordinateur client. Modules de fusion (fichiers .msm) ne fournissent pas de ces garanties et ne doivent pas être utilisés.  
  
### <a name="accounting-for-custom-actions"></a>Gestion des comptes pour les Actions personnalisées  
 Actions personnalisées sont des directives d’installation non standard dans un programme d’installation. Actions personnalisées modifier des paramètres tels que les emplacements de fichiers, paramètres du Registre, les paramètres utilisateur ou autres éléments d’installation. Actions personnalisées peuvent manipuler des données au moment de l’installation.  
  
 Lorsque vous utilisez des actions personnalisées dans un programme d’installation, vous devez vous assurer que chaque action personnalisée au moment de l’installation doit avoir une action personnalisée correspondante pour annuler l’action lorsque l’utilisateur désinstalle l’application. Si votre programme d’installation échoue pour fournir correspondant désinstalle action personnalisée, suppression de votre application reste partiellement installé.  
  
- Une action personnalisée qui s’appuie sur une version spécifique d’un fichier ou le hachage de valeurs échoue lors de la modification de ces versions de mises à jour logicielles ou valeurs de hachage. Dans ce cas votre action personnalisée doit mettre à jour manuellement ces valeurs. Un autre problème se produit si les versions d’un fichier ou le hachage de valeurs sont partagées entre les versions de produit. Évitez cette dépendance chaque fois que possible.  
  
### <a name="accounting-for-shared-files"></a>Gestion des comptes pour les fichiers partagés  
 Fichiers partagés ont les mêmes noms et sont installés au même emplacement par plusieurs produits. Ces produits peuvent différer dans la version, référence (SKU Stock Keeping Unit) ou les deux, et les produits peuvent coexister sur un ordinateur donné. Toutefois, les fichiers partagés créer des problèmes de maintenance pour plusieurs raisons :  
  
- La mise à jour des fichiers partagés peut entraîner des problèmes de compatibilité des applications, car une mise à jour à une application peut changer la version d’un fichier utilisé par une autre application n’a pas été mis à jour. Programmes d’installation pour les produits qui partagent des références de nombre de fichiers pour les fichiers partagés. Par conséquent, la désinstallation d’un produit n’affecte pas les fichiers partagés au-delà de décrémenter le nombre d’instances installées.  
  
- Le programme d’installation de l’ingénierie QFE (Quick Fix) rétablit les versions des fichiers pour les versions des produits pris en charge par le programme d’installation du correctif QFE. Ce processus potentiellement s'arrête une application qui a remis un fichier partagé mis à jour.
