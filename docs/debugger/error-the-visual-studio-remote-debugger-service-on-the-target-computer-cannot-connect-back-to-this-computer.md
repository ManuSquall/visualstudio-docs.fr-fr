---
title: "Erreur : Le service Débogueur distant Visual Studio sur l'ordinateur cible ne peut pas se reconnecter à cet ordinateur"
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 695c4c9e84ce9eb851a551dc9821bff00123a35c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737410"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Erreur : Le service Débogueur distant Visual Studio sur l'ordinateur cible ne peut pas se reconnecter à cet ordinateur
Cette erreur signifie que le service du débogueur distant s’exécute sous un compte d’utilisateur qui ne peut pas s’authentifier lorsqu’il tente de se connecter à l’ordinateur à partir duquel vous déboguez. Cette erreur peut se produire lors du débogage à distance à l’aide du moteur de débogage hérité et que le débogueur distant s’exécute en tant que service.

 Le tableau suivant répertorie les comptes autorisés à accéder à l'ordinateur:

|||||
|-|-|-|-|
||Compte LocalSystem|Compte de domaine|Comptes locaux avec les mêmes nom d'utilisateur et mot de passe sur les deux ordinateurs|
|Deux ordinateurs sur le même domaine|Oui|Oui|Oui|
|Deux ordinateurs sur des domaines qui ont un niveau de confiance bidirectionnel|Non|Non|Oui|
|Un ordinateur, ou les deux, dans un groupe de travail|Non|Non|Oui|
|Ordinateurs sur des domaines différents|Non|Non|Oui|

 En outre :

- Le compte sous lequel vous exécutez le service Débogueur distant Visual Studio doit être un administrateur sur l'ordinateur distant afin qu'il puisse déboguer tout processus.

- Le privilège `Log on as a service` doit également être accordé au compte sur l’ordinateur distant qui utilise l’outil d’administration **Stratégie de sécurité locale**.

- Si vous utilisez un compte local pour accéder à l'ordinateur, vous devez exécuter le service Débogueur distant Visual Studio sous un compte local.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que le service Débogueur distant Visual Studio est correctement installé sur l'ordinateur distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).

2. Exécutez le service Débogueur distant sous un compte qui peut accéder à l'ordinateur hôte du débogueur, comme indiqué dans le tableau précédent.

### <a name="to-add-log-on-as-a-service-privilege"></a>Pour ajouter le privilège « Ouvrir une session en tant que service »

1. Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.

2. Dans le Panneau de configuration, cliquez sur **Affichage classique**, si nécessaire.

3. Double-cliquez sur **Outils d'administration**.

4. Dans la fenêtre Outils d’administration, double-cliquez sur **Stratégie de sécurité locale**.

5. Dans la fenêtre **Paramètres de sécurité locaux**, développez le dossier **Stratégies locales**.

6. Cliquez sur **Attribution des droits utilisateur**.

7. Dans la colonne **Stratégie**, double-cliquez sur **Ouvrir une session en tant que service** pour afficher les affectations de la stratégie de groupe locale dans la boîte de dialogue **Ouvrir une session en tant que service**.

8. Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.

9. Après avoir ajouté les utilisateurs de votre choix, cliquez sur **OK**.

### <a name="to-work-around-this-error"></a>Pour contourner cette erreur

- Exécutez le Remote Debugging Monitor comme une application au lieu d'un service.

## <a name="see-also"></a>Voir aussi
- [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)