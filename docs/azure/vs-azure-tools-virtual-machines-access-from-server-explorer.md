---
title: Accès aux machines virtuelles Azure à partir de l’Explorateur de serveurs | Microsoft Docs
description: Obtenez une présentation de l’affichage, de la création et de la gestion des machines virtuelles Azure dans l’Explorateur de serveurs de Visual Studio.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 653a9be556441f5f8d5fc1c1053b144dc97dd3b2
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901868"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Accès aux machines virtuelles Azure à partir de l’Explorateur de serveurs

Si vous avez des machines virtuelles hébergées par Azure, vous pouvez y accéder depuis l’Explorateur de serveurs. Vous devez d’abord vous connecter à votre abonnement Azure pour afficher vos services mobiles. Pour vous connecter, ouvrez le menu contextuel du nœud Azure dans l’Explorateur de serveurs, puis choisissez **Se connecter à Microsoft Azure**.

1. Dans Cloud Explorer, choisissez une machine virtuelle, puis appuyez sur la touche F4 pour afficher sa fenêtre de propriétés.

    Le tableau suivant indique les propriétés disponibles. Toutes les propriétés sont en lecture seule. Utilisez le [portail Azure](https://portal.azure.com) pour les changer.

   | Propriété | Description |
   | --- | --- |
   | Nom DNS |URL comportant l’adresse Internet de la machine virtuelle. |
   | Environnement |Pour une machine virtuelle, la valeur de cette propriété est toujours Production. |
   | Nom |Nom de la machine virtuelle. |
   | Taille |Taille de la machine virtuelle, qui reflète la quantité de mémoire et d’espace disque disponibles. Pour plus d’informations, consultez [tailles de machines virtuelles](/azure/cloud-services/cloud-services-sizes-specs). |
   | Statut |Les valeurs incluent : Démarrage en cours, Démarré, En cours d’arrêt, Arrêté et Extraction de l’état. Si Extraction de l’état s’affiche, l’état actuel est inconnu. Les valeurs de cette propriété ne sont pas les mêmes que celles qui sont utilisées dans le [portail Azure](https://portal.azure.com). |
   | SubscriptionID |ID d’abonnement de votre compte Azure. Vous pouvez obtenir cette information sur le [portail Azure](https://portal.azure.com) en affichant les propriétés de l’abonnement. |
2. Sélectionnez un nœud de point de terminaison, puis affichez la fenêtre **Propriétés**.
3. Le tableau suivant décrit les propriétés des points de terminaison disponibles. Toutes ces propriétés sont en lecture seule. Pour ajouter ou modifier les points de terminaison d’une machine virtuelle, utilisez le [portail Azure](https://portal.azure.com).

   | Propriété | Description |
   | --- | --- |
   | Nom |Identificateur du point de terminaison. |
   | Port privé |Port d’accès réseau interne à votre application. |
   | Protocol |Protocole utilisé par la couche de transport du point de terminaison (TCP ou UDP). |
   | Port public |Port utilisé pour l’accès public à votre application. |
