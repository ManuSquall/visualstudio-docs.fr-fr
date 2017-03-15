---
title: "Erreur&#160;: Le service D&#233;bogueur distant Visual Studio sur l&#39;ordinateur cible ne peut pas se reconnecter &#224; cet ordinateur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.service_access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Le service D&#233;bogueur distant Visual Studio sur l&#39;ordinateur cible ne peut pas se reconnecter &#224; cet ordinateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette erreur signifie que le service Débogueur distant Visual Studio s'exécute sous un compte d'utilisateur qui ne peut pas être authentifié lorsqu'il se connecte à l'ordinateur à partir duquel vous déboguez.  
  
 Le tableau suivant répertorie les comptes autorisés à accéder à l'ordinateur:  
  
|||||  
|-|-|-|-|  
||Compte LocalSystem|Compte de domaine|Comptes locaux avec les mêmes nom d'utilisateur et mot de passe sur les deux ordinateurs|  
|Deux ordinateurs sur le même domaine|Oui|Oui|Oui|  
|Deux ordinateurs sur des domaines qui ont un niveau de confiance bidirectionnel|Non|Non|Oui|  
|Un ordinateur, ou les deux, dans un groupe de travail|Non|Non|Oui|  
|Ordinateurs sur des domaines différents|Non|Non|Oui|  
  
 De plus :  
  
-   Le compte sous lequel vous exécutez le service Débogueur distant Visual Studio doit être un administrateur sur l'ordinateur distant afin qu'il puisse déboguer tout processus.  
  
-   Le privilège `Log on as a service` doit également être accordé au compte sur l'ordinateur distant qui utilise l'outil d'administration **Stratégie de sécurité locale**.  
  
-   Si vous utilisez un compte local pour accéder à l'ordinateur, vous devez exécuter le service Débogueur distant Visual Studio sous un compte local.  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que le service Débogueur distant Visual Studio est correctement installé sur l'ordinateur distant.  Pour plus d'informations, consultez [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
2.  Exécutez le service Débogueur distant sous un compte qui peut accéder à l'ordinateur hôte du débogueur, comme indiqué dans le tableau précédent.  
  
### Pour ajouter le privilège « Ouvrir une session en tant que service »  
  
1.  Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, cliquez sur **Affichage classique**, si nécessaire.  
  
3.  Double\-cliquez sur **Outils d'administration**.  
  
4.  Dans la fenêtre Outils d'administration, double\-cliquez sur **Stratégie de sécurité locale**.  
  
5.  Dans la fenêtre **Paramètres de sécurité locaux**, développez le dossier **Stratégies locales**.  
  
6.  Cliquez sur **Attribution des droits utilisateur**.  
  
7.  Dans la colonne **Stratégie**, double\-cliquez sur **Ouvrir une session en tant que service** pour afficher les affectations de la stratégie de groupe locale dans la boîte de dialogue **Ouvrir une session en tant que service**.  
  
8.  Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.  
  
9. Après avoir ajouté les utilisateurs de votre choix, cliquez sur **OK**.  
  
### Pour contourner cette erreur  
  
-   Exécutez le Remote Debugging Monitor comme une application au lieu d'un service.  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage distant](../debugger/remote-debugging.md)