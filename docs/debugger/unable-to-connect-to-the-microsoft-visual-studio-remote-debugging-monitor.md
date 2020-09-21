---
title: Impossible de se connecter à l'ordinateur Microsoft Visual Studio Remote Debugging Monitor
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
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
ms.openlocfilehash: 63bd6fba7305c8dd266ecc935ea00d04633c6aec
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809334"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossible de se connecter à l'ordinateur Microsoft Visual Studio Remote Debugging Monitor
Ce message peut s’afficher, car le moniteur de débogage à distance n’est pas correctement configuré sur l’ordinateur distant ou l’ordinateur distant est inaccessible en raison de problèmes réseau ou de la présence d’un pare-feu.

> [!IMPORTANT]
> Si vous pensez que vous avez reçu ce message en raison d’un bogue produit, veuillez [signaler ce problème](../ide/how-to-report-a-problem-with-visual-studio.md) à Visual Studio. Si vous avez besoin d’aide supplémentaire, consultez [Talk to Us](../ide/feedback-options.md) pour savoir comment contacter Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Quel est le message d’erreur détaillé ?

Le `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` message est générique. En règle générale, un message plus spécifique est inclus dans la chaîne d’erreur et peut vous aider à identifier la cause du problème ou à rechercher un correctif plus exact. Voici quelques-uns des messages d’erreur les plus courants qui sont ajoutés au message d’erreur principal :

- [Le débogueur ne peut pas se connecter à l’ordinateur distant. Le débogueur n’a pas pu résoudre le nom de l’ordinateur spécifié](#cannot_connect)
- [La demande de connexion a été rejetée par le débogueur distant](#rejected)
- [La connexion avec le point de terminaison distant a été arrêtée](#connection_terminated)
- [Accès non valide à l’emplacement de la mémoire](#invalid_access)
- [Il n’existe aucun serveur du nom spécifié en cours d’exécution sur l’ordinateur distant](#no_server)
- [Le nom demandé est valide, mais aucune donnée du type demandé n’a été trouvée](#valid_name)
- [Le Débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur](#cant_connect_back)
- [Accès refusé](#access_denied)
- [Une erreur spécifique au package de sécurité s’est produite](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Le débogueur ne peut pas se connecter à l’ordinateur distant. Le débogueur n’a pas pu résoudre le nom de l’ordinateur spécifié

Essayez d’effectuer les étapes suivantes :

1. Veillez à entrer un nom d’ordinateur et un numéro de port valides dans la boîte de dialogue **attacher au processus** ou dans les propriétés du projet (pour définir les propriétés, consultez [ces étapes](#server_incorrect)). Le nom de l’ordinateur doit être au format suivant :

    `computername:port`

    > [!NOTE]
    > Le numéro de port doit correspondre au [numéro de port du débogueur distant](../debugger/remote-debugger-port-assignments.md), qui *doit être en cours d’exécution* sur l’ordinateur cible.

2. Si le nom de l’ordinateur ne fonctionne pas, essayez plutôt l’adresse IP et le numéro de port.

3. Assurez-vous que la version du débogueur distant en cours d’exécution sur l’ordinateur cible correspond à votre version de Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

    > [!TIP]
    > Si vous êtes connecté au processus et que vous vous connectez avec succès mais que vous ne voyez pas le processus que vous souhaitez, activez la case **à cocher Afficher les processus de tous les utilisateurs**. Cette opération affiche les processus si vous êtes connecté sous un compte d’utilisateur différent.

4. Si ces étapes ne résolvent pas cette erreur, consultez [la machine distante n’est pas accessible](#dns).

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> La demande de connexion a été rejetée par le débogueur distant

Dans la boîte de dialogue **attacher au processus** ou dans les propriétés du projet, assurez-vous que le nom de l’ordinateur distant et le numéro de port correspondent au nom et au numéro de port indiqués dans la fenêtre du débogueur distant. Si ce n’est pas le cas, corrigez et réessayez.

Si ces valeurs sont correctes et que le message mentionne le mode **d’authentification Windows** , vérifiez que le débogueur distant est dans le mode d’authentification correct (**Outils > options**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> La connexion avec le point de terminaison distant a été arrêtée

Si vous déboguez une application Azure App Service, essayez d’utiliser la commande [attacher le débogueur](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) à partir de Cloud Explorer ou Explorateur de serveurs au lieu de **attacher au processus**.

Si vous utilisez **attacher au processus** pour déboguer :

- Dans la boîte de dialogue **attacher au processus** ou dans les propriétés du projet, assurez-vous que le nom de l’ordinateur distant et le numéro de port correspondent au nom et au numéro de port indiqués dans la fenêtre du débogueur distant. Si ce n’est pas le cas, corrigez et réessayez.

- Si vous essayez de vous connecter à l’aide d’un nom d’hôte, essayez une adresse IP à la place.

- Pour plus d’informations sur la résolution du problème, consultez le journal des applications sur le serveur (observateur d’événements sur Windows).

- Dans le cas contraire, essayez de redémarrer Visual Studio avec des privilèges d’administrateur, puis réessayez.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Accès non valide à l’emplacement de la mémoire

Une erreur interne s’est produite. Redémarrez Visual Studio et recommencez.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Il n’existe aucun serveur du nom spécifié en cours d’exécution sur l’ordinateur distant

Visual Studio n’a pas pu se connecter au débogueur distant. Ce message peut s’afficher pour plusieurs raisons :

- Le débogueur distant peut s’exécuter sous un compte d’utilisateur différent. Consultez [ces étapes](#user_accounts)

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu ne [bloque pas votre demande](#firewall), surtout si vous utilisez un pare-feu tiers.

- La version du débogueur distant ne correspond pas à Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> Le nom demandé est valide, mais aucune donnée du type demandé n’a été trouvée

L’ordinateur distant existe, mais Visual Studio n’a pas pu se connecter au débogueur distant. Ce message peut s’afficher pour plusieurs raisons :

- Un problème DNS empêche la connexion. Consultez [ces étapes](#dns).

- Le débogueur distant peut s’exécuter sous un compte d’utilisateur différent. Procédez comme [suit](#user_accounts).

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu ne [bloque pas votre demande](#firewall), surtout si vous utilisez un pare-feu tiers.

- La version du débogueur distant ne correspond pas à Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a> Le Débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur

Le débogueur distant peut s’exécuter sous un compte d’utilisateur différent. Dans le débogueur distant, ouvrez **outils > autorisations** pour ajouter l’utilisateur aux autorisations du débogueur distant. Pour plus d’informations, consultez [le débogueur distant s’exécute sous un compte d’utilisateur différent](#user_accounts).

Si le message d’erreur mentionne également un pare-feu, le pare-feu sur l’ordinateur local peut empêcher la communication entre l’ordinateur distant et Visual Studio. Consultez [ces étapes](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a> Accès refusé

Cette erreur peut s’afficher si vous essayez de déboguer sur un ordinateur distant 64 bits à partir d’un ordinateur 32 bits (non pris en charge).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Une erreur spécifique au package de sécurité s’est produite

Il peut s’agir d’un problème hérité spécifique à Windows XP et Windows 7. Consultez ces [informations](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causes et recommandations

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> L’ordinateur distant n’est pas accessible

Si vous ne pouvez pas vous connecter à l’aide du nom de l’ordinateur distant, essayez d’utiliser l’adresse IP à la place. Vous pouvez utiliser `ipconfig` dans une ligne de commande sur l’ordinateur distant pour obtenir l’adresse IPv4. Si vous utilisez un fichier HOSTs, vérifiez qu’il est correctement configuré.

En cas d’échec, vérifiez que l’ordinateur distant est accessible sur le réseau (effectuez un[test ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) sur l’ordinateur distant). Le débogage distant sur Internet n’est pas pris en charge, sauf dans certains scénarios de Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Le nom du serveur est incorrect ou un logiciel tiers interfère avec le débogueur distant

Dans Visual Studio, examinez les propriétés du projet et assurez-vous que le nom du serveur est correct. Consultez les rubriques pour [C# et Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) et [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Pour ASP.NET, ouvrez **Propriétés/Web/serveurs** ou **Propriétés/déboguer** en fonction de votre type de projet.

> [!NOTE]
> Si vous effectuez un attachement au processus, les paramètres distants dans les propriétés du projet ne sont pas utilisés.

Si le nom du serveur est correct, votre logiciel antivirus ou un pare-feu tiers peut bloquer le débogueur distant. En cas de débogage local, cela peut se produire si Visual Studio est une application 32 bits, de sorte qu’elle utilise la version 64 bits du débogueur distant pour déboguer des applications 64 bits. Les processus 32 bits et 64 bits communiquent à l’aide du réseau local au sein de l’ordinateur local. Aucun trafic réseau ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Le débogueur distant s’exécute sous un compte d’utilisateur différent

Par défaut, le débogueur distant n’accepte que les connexions de l’utilisateur qui a lancé le débogueur distant et les membres du groupe administrateurs. Des autorisations doivent être explicitement accordées aux utilisateurs supplémentaires.

Pour résoudre ce problème, vous pouvez procéder de différentes façons :

- Ajoutez l’utilisateur Visual Studio aux autorisations du débogueur distant (dans la fenêtre du débogueur distant, choisissez **outils > autorisations**).

- Sur l’ordinateur distant, redémarrez le débogueur distant sous le même compte d’utilisateur et le même mot de passe que vous utilisez sur l’ordinateur Visual Studio.

    > [!NOTE]
    > Si vous exécutez le débogueur distant sur un serveur distant, cliquez avec le bouton droit sur l’application du débogueur distant et choisissez **exécuter en tant qu’administrateur** (ou, vous pouvez exécuter le débogueur distant en tant que service). Si vous ne l’exécutez pas sur un serveur distant, il vous suffit de le démarrer normalement.

- Vous pouvez démarrer le débogueur distant à partir de la ligne de commande avec le paramètre **/allow \<username> ** : `msvsmon /allow <username@computer>` .

- Vous pouvez également autoriser n’importe quel utilisateur à effectuer un débogage distant. Dans la fenêtre du débogueur distant, accédez à la boîte de dialogue **Outils > Options**. Quand vous sélectionnez   **Aucune authentification**, vous pouvez ensuite cocher **Permettre à tous les utilisateurs de déboguer**. Toutefois, vous devez essayer cette option uniquement si les autres options échouent, ou si vous êtes sur un réseau privé.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Le pare-feu sur l’ordinateur distant n’autorise pas les connexions entrantes au débogueur distant
 Le pare-feu sur l’ordinateur Visual Studio et celui sur l’ordinateur distant doivent être configurés pour autoriser la communication entre Visual Studio et le débogueur distant. Pour plus d’informations sur les ports utilisés par le débogueur distant, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Pour plus d’informations sur la configuration du Pare-feu Windows, consultez [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La version du débogueur distant ne correspond pas à la version de Visual Studio
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Les ordinateurs locaux et distants utilisent des modes d’authentification différents
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez-vous que les deux ordinateurs utilisent le même mode d’authentification. Vous pouvez modifier le mode d’authentification. Dans la fenêtre du débogueur distant, accédez à la boîte de dialogue **outils > options** .

 Pour plus d’informations sur les modes d’authentification, consultez [Vue d’ensemble de l’authentification Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Un antivirus bloque les connexions
 L’antivirus Windows autorise les connexions au débogueur distant, mais certains antivirus tiers peuvent les bloquer. Consultez la documentation de votre antivirus pour savoir comment autoriser ces connexions.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La stratégie de sécurité réseau bloque la communication entre l’ordinateur distant et Visual Studio
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la stratégie de sécurité réseau Windows, consultez [paramètres de stratégie de sécurité](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Le réseau est trop occupé pour prendre en charge le débogage distant
 Dans ce cas, vous devrez peut-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.

## <a name="more-help"></a>Aide supplémentaire
 Pour obtenir plus d’informations sur l’aide du débogueur distant, ouvrez la page d’aide du débogueur distant (**aide > l’utilisation** dans le débogueur distant).

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)
