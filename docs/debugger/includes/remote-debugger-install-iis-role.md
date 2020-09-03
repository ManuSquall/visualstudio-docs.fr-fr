---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324349"
---
Ces étapes affichent uniquement une configuration de base d’IIS. Pour obtenir des informations plus approfondies ou pour installer sur un ordinateur de bureau Windows, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [IIS 8,0 à l’aide de ASP.NET 3,5 et ASP.net 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Pour les systèmes d’exploitation Windows Server, utilisez l’Assistant **Ajout de rôles et de fonctionnalités** via le lien **gérer** ou **tableau de bord** dans **Gestionnaire de serveur**. À l’étape **Rôles de serveurs**, cochez la case **Serveur Web (IIS)**.

![Le rôle Serveur Web IIS est sélectionné à l’étape Sélectionner des rôles de serveurs.](../media/remotedbg-server-roles-ws2012.png)

À l’étape **Services de rôle**, sélectionnez les services de rôle IIS souhaités ou acceptez les services de rôle par défaut. Si vous souhaitez activer le déploiement à l’aide des paramètres de publication et de la Web Deploy, assurez-vous que l’option **scripts et outils de gestion IIS** est sélectionnée.

Suivez les étapes de confirmation pour installer le rôle de serveur Web et les services. Un redémarrage du serveur/d’IIS n’est pas nécessaire après l’installation du rôle Serveur Web (IIS).