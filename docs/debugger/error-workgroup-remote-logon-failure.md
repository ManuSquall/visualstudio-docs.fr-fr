---
title: 'Erreur : échec d’ouverture de session à distance du groupe de travail | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97045215098b1f59d5f76a928e9e0a1ab8362756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460090"
---
# <a name="error-workgroup-remote-logon-failure"></a>Erreur : Échec d'ouverture de session à distance du groupe de travail
Cette erreur affiche le message suivant :

 Échec d'ouverture de session : nom d'utilisateur inconnu ou mot de passe incorrect

 **Cause**

 Cette erreur peut se produire lorsque vous déboguez à partir d'un ordinateur au sein d'un groupe de travail et que vous tentez de vous connecter à un ordinateur distant. Les causes possibles sont les suivantes :

- Il n'existe pas de compte avec le nom et le mot de passe correspondants sur l'ordinateur distant.

- Si l’ordinateur Visual Studio et l’ordinateur distant appartiennent à des groupes de travail, cette erreur peut se produire en raison du paramètre par défaut **Stratégie de sécurité locale** sur l’ordinateur distant. L’option par défaut du paramètre **Stratégie de sécurité locale** est **Invité seul - les utilisateurs locaux s’authentifient en tant qu’invités**. Pour effectuer un débogage sur cette installation, vous devez remplacer le paramètre sur l’ordinateur distant par **Classique - les utilisateurs locaux s’authentifient eux-mêmes**.

> [!NOTE]
> Vous devez être administrateur pour exécuter les tâches suivantes.

### <a name="to-open-the-local-security-policy-window"></a>Pour ouvrir la fenêtre Stratégie de sécurité locale

1. Démarrez le composant logiciel enfichable Microsoft Management Console **secpol.msc**. Tapez secpol.msc dans la zone de recherche Windows, dans la zone Exécuter de Windows, ou dans une invite de commandes.

### <a name="to-add-user-rights-assignments"></a>Pour ajouter des assignations de droits utilisateur

1. Ouvrez la fenêtre **Stratégie de sécurité locale**.

2. Développez le dossier **Stratégies locales**.

3. Cliquez sur **Attribution des droits utilisateur**.

4. Dans la colonne **Stratégie**, double-cliquez sur **Déboguer des programmes pour afficher les assignations de la stratégie de groupe locale** dans la boîte de dialogue **Paramètre de stratégie de sécurité locale**.

     ![Droits d’utilisateur de stratégie de sécurité locale](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.

### <a name="to-change-the-sharing-and-security-model"></a>Pour modifier le modèle de partage et de sécurité

1. Ouvrez la fenêtre **Stratégie de sécurité locale**.

2. Développez le dossier **Stratégies locales**.

3. Cliquez sur **Options de sécurité**.

4. Dans la colonne **Stratégie**, double-cliquez sur **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**.

5. Dans la boîte de dialogue **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**, remplacez la valeur par **Classique - les utilisateurs locaux s’authentifient eux-mêmes** et cliquez sur le bouton **Appliquer**.

     ![Options de sécurité de stratégie de sécurité locale](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Voir aussi
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Débogage à distance](../debugger/remote-debugging.md)