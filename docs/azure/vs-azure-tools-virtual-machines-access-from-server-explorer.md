---
title: Accès aux machines virtuelles Azure à partir de l’Explorateur de serveurs | Microsoft Docs
description: Obtenez une présentation de l’affichage, de la création et de la gestion des machines virtuelles Azure dans l’Explorateur de serveurs de Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: ab67a81d761f2e17c82b75fb59a201188cf80986
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997629"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Accès aux machines virtuelles Azure à partir de l’Explorateur de serveurs

::: moniker range=">=vs-2022"
> [!Important]
> Le nœud Azure de Explorateur de serveurs a été mis hors service dans Visual Studio 2022. Vous pouvez utiliser le portail Azure ou continuer à utiliser le nœud Azure de Explorateur de serveurs dans les versions précédentes de Visual Studio.
>
> En outre, [Explorateur stockage Microsoft Azure](/azure/vs-azure-tools-storage-manage-with-storage-explorer) est une application autonome et gratuite de Microsoft. Vous pouvez l’utiliser pour travailler visuellement avec les données du stockage Azure sur Windows, macOS et Linux.
>
> Pour plus d’informations sur Visual Studio 2022, consultez nos [notes de publication](/visualstudio/releases/2022/release-notes-preview/).

::: moniker-end

::: moniker range="<=vs-2017"

Si vous avez des machines virtuelles hébergées par Azure, vous pouvez y accéder depuis l’Explorateur de serveurs. Vous devez d’abord vous connecter à votre abonnement Azure pour afficher vos services mobiles. Pour vous connecter, ouvrez le menu contextuel du nœud Azure dans l’Explorateur de serveurs, puis choisissez **Se connecter à Microsoft Azure**.

1. Dans Cloud Explorer, choisissez une machine virtuelle, puis appuyez sur la touche F4 pour afficher sa fenêtre de propriétés.

    Le tableau suivant indique les propriétés disponibles. Toutes les propriétés sont en lecture seule. Utilisez le [portail Azure](https://portal.azure.com) pour les changer.

   | Propriété | Description |
   | --- | --- |
   | Nom DNS |URL comportant l’adresse Internet de la machine virtuelle. |
   | Environnement |Pour une machine virtuelle, la valeur de cette propriété est toujours Production. |
   | Nom |Nom de la machine virtuelle. |
   | Taille |Taille de la machine virtuelle, qui reflète la quantité de mémoire et d’espace disque disponibles. Pour plus d’informations, consultez [tailles de machines virtuelles](/azure/cloud-services/cloud-services-sizes-specs). |
   | État |Les valeurs incluent : Démarrage en cours, Démarré, En cours d’arrêt, Arrêté et Extraction de l’état. Si Extraction de l’état s’affiche, l’état actuel est inconnu. Les valeurs de cette propriété ne sont pas les mêmes que celles qui sont utilisées dans le [portail Azure](https://portal.azure.com). |
   | SubscriptionID |ID d’abonnement de votre compte Azure. Vous pouvez obtenir cette information sur le [portail Azure](https://portal.azure.com) en affichant les propriétés de l’abonnement. |
2. Sélectionnez un nœud de point de terminaison, puis affichez la fenêtre **Propriétés**.
3. Le tableau suivant décrit les propriétés des points de terminaison disponibles. Toutes ces propriétés sont en lecture seule. Pour ajouter ou modifier les points de terminaison d’une machine virtuelle, utilisez le [portail Azure](https://portal.azure.com).

   | Propriété | Description |
   | --- | --- |
   | Nom |Identificateur du point de terminaison. |
   | Port privé |Port d’accès réseau interne à votre application. |
   | Protocole |Protocole utilisé par la couche de transport du point de terminaison (TCP ou UDP). |
   | Port public |Port utilisé pour l’accès public à votre application. |

::: moniker-end