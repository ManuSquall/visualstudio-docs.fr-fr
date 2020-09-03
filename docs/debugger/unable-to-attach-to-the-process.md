---
title: Impossible de s’attacher au processus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
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
ms.openlocfilehash: 22d798d30d09cb509f53d093ae61bb1a02b414ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728873"
---
# <a name="unable-to-attach-to-the-process"></a>Impossible de s'attacher au processus
Impossible de s'attacher au processus Le composant Débogueur sur le serveur s'est vu refuser l'accès pendant la connexion à cet ordinateur.

 Deux scénarios courants peuvent être à l'origine de cette erreur :

 **Scénario 1 :** L’ordinateur A exécute Windows XP. L'ordinateur B exécute Windows Server 2003. Le registre de l'ordinateur B contient la valeur DWORD suivante :

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 L'utilisateur 1 démarre une session Terminal Server (session 1) sur l'ordinateur B et démarre une application managée à partir de cette session.

 L’utilisateur 2, qui est administrateur sur les deux ordinateurs, est connecté à l’ordinateur A. À partir de là, il tente de s’attacher à une application exécutée dans la session 1 sur l’ordinateur B.

 **Scénario 2 :** Un utilisateur a ouvert une session sur deux ordinateurs, A et B, dans le même groupe de travail, avec le même mot de passe sur les deux ordinateurs. Le débogueur s’exécute sur l’ordinateur A et tente de s’attacher à une application managée s’exécutant sur l’ordinateur B. l’ordinateur a a **accès réseau : modèle de partage et de sécurité pour les comptes locaux** définis sur **invité**.

### <a name="to-solve-scenario-1"></a>Pour résoudre le scénario 1

- Exécutez le débogueur et l'application managée avec le même nom de compte d'utilisateur et le même mot de passe.

### <a name="to-solve-scenario-2"></a>Pour résoudre le scénario 2

1. Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.

2. Dans le Panneau de configuration, double-cliquez sur **Outils d’administration**.

3. Dans la fenêtre outils d’administration, double-cliquez sur **stratégie de sécurité locale**.

4. Dans la fenêtre Stratégie de sécurité locale, sélectionnez **Stratégies locales**.

5. Dans la colonne **Stratégies**, double-cliquez sur **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**.

6. Dans la boîte de dialogue **Accès réseau : modèle de partage et de sécurité pour les comptes locaux**, remplacez le paramètre de sécurité locale par **Classique** et cliquez sur **OK**.

    > [!CAUTION]
    > Changer le modèle de sécurité en Classique peut engendrer un accès inattendu à des fichiers partagés et aux composants DCOM. Si vous apportez cette modification, un utilisateur distant peut s'authentifier avec votre compte d'utilisateur local plutôt qu'avec un compte Invité. Si un utilisateur distant correspond à votre nom d’utilisateur et à votre mot de passe, il peut accéder à tout dossier ou objet DCOM que vous avez partagé. Si vous utilisez ce modèle de sécurité, assurez-vous que tous les comptes d’utilisateur sur l’ordinateur ont des mots de passe forts ou configurez un îlot de réseau isolé pour les ordinateurs de débogage et débogués afin d’empêcher tout accès non autorisé.

7. Fermez toutes les fenêtres.

## <a name="see-also"></a>Voir aussi
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)