---
title: "Erreur&#160;: &#201;chec d&#39;ouverture de session &#224; distance du groupe de travail | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.workgroup_remote_logon_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "échec d'ouverture de session, débogage distant"
  - "débogage distant, échec d'ouverture de session"
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Erreur&#160;: &#201;chec d&#39;ouverture de session &#224; distance du groupe de travail
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette erreur affiche le message suivant :  
  
 Échec d'ouverture de session : nom d'utilisateur inconnu ou mot de passe incorrect  
  
 **Cause**  
  
 Cette erreur peut se produire lorsque vous déboguez à partir d'un ordinateur au sein d'un groupe de travail et que vous tentez de vous connecter à un ordinateur distant.  Plusieurs causes sont possibles :  
  
-   Il n'existe pas de compte avec le nom et le mot de passe correspondants sur l'ordinateur distant.  
  
-   Si l'ordinateur Visual Studio et l'ordinateur distant appartiennent à des groupes de travail, cette erreur peut se produire en raison du paramètre par défaut **Stratégie de sécurité locale** sur l'ordinateur distant.  L'option par défaut du paramètre **Stratégie de sécurité locale** est **Invité seul \- les utilisateurs locaux s'authentifient en tant qu'invités**.  Pour effectuer un débogage sur cette installation, vous devez remplacer le paramètre sur l'ordinateur distant par **Classique \- les utilisateurs locaux s'authentifient eux\-mêmes.**  
  
> [!NOTE]
>  Vous devez être administrateur pour exécuter les tâches suivantes.  
  
### Pour ouvrir la fenêtre Stratégie de sécurité locale  
  
1.  Démarrez le composant logiciel enfichable Microsoft Management Console **secpol.msc**.  Tapez secpol.msc dans la zone de recherche Windows, dans la zone Exécuter de Windows, ou dans une invite de commandes.  
  
### Pour ajouter des assignations de droits utilisateur  
  
1.  Ouvrez les Paramètres régionaux  
  
2.  Ouvrez la fenêtre **Stratégie de sécurité locale**.  
  
3.  Développez le dossier **Stratégies locales**.  
  
4.  Cliquez sur **Attribution des droits utilisateur**.  
  
5.  Dans la colonne **Policy**, double\-cliquez sur **Déboguer des programmes** pour afficher les assignations de la stratégie de groupe locale dans la boîte de dialogue **Paramètre de stratégie de sécurité locale**.  
  
     ![Droits d’utilisateur de stratégie de sécurité locale](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG\_ERR\_LocalSecurityPolicy\_UserRightsDebugPrograms")  
  
6.  Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.  
  
### Pour modifier le modèle de partage et de sécurité  
  
1.  Ouvrez la fenêtre **Stratégie de sécurité locale**.  
  
2.  Développez le dossier **Stratégies locales**.  
  
3.  Cliquez sur **Options de sécurité**.  
  
4.  Dans la colonne **Stratégie**, double\-cliquez sur **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**.  
  
5.  Dans la boîte de dialogue **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**, remplacez la valeur par **Classique \- les utilisateurs locaux s'authentifient eux\-mêmes** et cliquez sur le bouton **Appliquer**.  
  
     ![Options de sécurité de stratégie de sécurité locale](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG\_ERR\_LocalSecurityPolicy\_SecurityOptions\_NetworkAccess")  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage distant](../debugger/remote-debugging.md)