---
title: L’accès aux Machines virtuelles à partir de l’Explorateur de serveurs | Microsoft Docs
description: Obtenir une vue d’ensemble de l’affichage créer et gérer des machines virtuelles Azure (VM) dans l’Explorateur de serveurs dans Visual Studio.
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001709"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Accès aux machines virtuelles Azure à partir de l’Explorateur de serveurs

Si vous avez des machines virtuelles hébergées par Azure, vous pouvez y accéder dans l’Explorateur de serveurs. Vous devez tout d’abord vous connecter à votre abonnement Azure pour afficher vos services mobiles. Pour vous connecter, ouvrez le menu contextuel du nœud Azure dans l’Explorateur de serveurs, puis choisissez **se connecter à Microsoft Azure**.

1. Dans Cloud Explorer, choisissez une machine virtuelle, puis la touche F4 pour afficher sa fenêtre de propriétés.

    Le tableau suivant montre quelles propriétés sont disponibles, mais ils sont en lecture seule. Pour les modifier, utilisez le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Propriété | Description |
   | --- | --- |
   | Nom DNS |L’URL avec l’adresse Internet de la machine virtuelle. |
   | Environnement |Pour une machine virtuelle, la valeur de cette propriété est toujours Production. |
   | Name |Le nom de la machine virtuelle. |
   | Size |La taille de la machine virtuelle, qui reflète la quantité de mémoire et espace disque disponible. Pour plus d’informations, consultez [tailles de Machine virtuelle](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Valeurs incluent le démarrage, démarré, l’arrêt, arrêté et extraction de l’état. Si l’extraction de l’état s’affiche, l’état actuel est inconnu. Les valeurs de cette propriété diffèrent des valeurs qui sont utilisés sur le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | ID d’abonnement |L’ID d’abonnement pour votre compte Azure. Vous pouvez afficher ces informations sur le [portail](http://go.microsoft.com/fwlink/p/?LinkID=525040) en affichant les propriétés d’un abonnement. |
2. Sélectionnez un nœud de point de terminaison et afficher le **propriétés** fenêtre.
3. Le tableau suivant décrit les propriétés des points de terminaison disponibles, mais ils sont en lecture seule. Pour ajouter ou modifier les points de terminaison pour un ordinateur virtuel, utilisez le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Propriété | Description |
   | --- | --- |
   | Name |Un identificateur pour le point de terminaison. |
   | Port privé |Le port pour l’accès réseau interne à votre application. |
   | Protocole |Le protocole utilisé par la couche de transport pour ce point de terminaison, TCP ou UDP. |
   | Port public |Le port qui est utilisé pour l’accès public à votre application. |
