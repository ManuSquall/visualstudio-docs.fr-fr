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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809443"
---
Ces étapes indiquent uniquement une configuration de base d’IIS. Pour plus d’informations ou pour installer sur un ordinateur de bureau de Windows, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Pour les systèmes d’exploitation Windows Server, utilisez le **Ajout de rôles et fonctionnalités** Assistant via la **gérer** lien ou le **tableau de bord** lier dans **leGestionnairedeserveur**. À l’étape **Rôles de serveurs**, cochez la case **Serveur Web (IIS)**.

![Le rôle Serveur Web IIS est sélectionné à l’étape Sélectionner des rôles de serveurs.](../media/remotedbg-server-roles-ws2012.png)

À l’étape **Services de rôle**, sélectionnez les services de rôle IIS souhaités ou acceptez les services de rôle par défaut. Si vous souhaitez activer le déploiement à l’aide de paramètres de publication et Web Deploy, assurez-vous que **gestion des Scripts et outils IIS** est sélectionné.

Exécutez les étapes de confirmation pour installer les services et le rôle de serveur web. Un redémarrage du serveur/d’IIS n’est pas nécessaire après l’installation du rôle Serveur Web (IIS).