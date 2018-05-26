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
ms.openlocfilehash: 62bdcd8109263cc86e13484d146e46f8e95c7198
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
Ces étapes indiquent uniquement une configuration de base d’IIS. Pour plus d’informations ou pour installer sur un ordinateur de bureau Windows, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Pour les systèmes d’exploitation Windows, utilisez le **Ajout de rôles et fonctionnalités** Assistant via la **gérer** lien ou le **tableau de bord** lien dans **leGestionnairedeserveur**. À l’étape **Rôles de serveurs**, cochez la case **Serveur Web (IIS)**.

![Le rôle Serveur Web IIS est sélectionné à l’étape Sélectionner des rôles de serveurs.](../media/remotedbg-server-roles-ws2012.png)

À l’étape **Services de rôle**, sélectionnez les services de rôle IIS souhaités ou acceptez les services de rôle par défaut. Si vous envisagez de déployer à l’aide de Web Deploy, assurez-vous que **gestion des Scripts et outils IIS** est sélectionnée.

Exécutez les étapes de confirmation pour installer les services et le rôle de serveur web. Un redémarrage du serveur/d’IIS n’est pas nécessaire après l’installation du rôle Serveur Web (IIS).