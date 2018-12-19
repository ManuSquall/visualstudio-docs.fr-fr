---
title: 'Erreur : Le service de débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37caaea1f70771145f318d892025d566a99f4ea6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062620"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Erreur : Le service de débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur
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
  
-   Le privilège `Log on as a service` doit également être accordé au compte sur l’ordinateur distant qui utilise l’outil d’administration **Stratégie de sécurité locale**.  
  
-   Si vous utilisez un compte local pour accéder à l'ordinateur, vous devez exécuter le service Débogueur distant Visual Studio sous un compte local.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que le service Débogueur distant Visual Studio est correctement installé sur l'ordinateur distant. Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
2.  Exécutez le service Débogueur distant sous un compte qui peut accéder à l'ordinateur hôte du débogueur, comme indiqué dans le tableau précédent.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Pour ajouter le privilège « Ouvrir une session en tant que service »  
  
1.  Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, cliquez sur **Affichage classique**, si nécessaire.  
  
3.  Double-cliquez sur **Outils d'administration**.  
  
4.  Dans la fenêtre Outils d’administration, double-cliquez sur **Stratégie de sécurité locale**.  
  
5.  Dans la fenêtre **Paramètres de sécurité locaux**, développez le dossier **Stratégies locales**.  
  
6.  Cliquez sur **Attribution des droits utilisateur**.  
  
7.  Dans la colonne **Stratégie**, double-cliquez sur **Ouvrir une session en tant que service** pour afficher les affectations de la stratégie de groupe locale dans la boîte de dialogue **Ouvrir une session en tant que service**.  
  
8.  Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.  
  
9. Après avoir ajouté les utilisateurs de votre choix, cliquez sur **OK**.  
  
### <a name="to-work-around-this-error"></a>Pour contourner cette erreur  
  
-   Exécutez le Remote Debugging Monitor comme une application au lieu d'un service.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)