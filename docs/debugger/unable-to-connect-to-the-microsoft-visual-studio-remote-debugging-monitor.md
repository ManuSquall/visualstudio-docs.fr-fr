---
title: Impossible de se connecter au Microsoft Visual Studio Remote Debugging Monitor (fr) Microsoft Docs
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
ms.openlocfilehash: d509292bc3c7a909289abf0c73babccfead31532
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385401"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossible de se connecter à l'ordinateur Microsoft Visual Studio Remote Debugging Monitor
Ce message peut se produire parce que le moniteur de débogage à distance n’est pas correctement configuré sur la machine à distance ou la machine à distance est inaccessible en raison de problèmes de réseau ou de la présence d’un pare-feu.

> [!IMPORTANT]
> Si vous croyez avoir reçu ce message en raison d’un bogue produit, veuillez [signaler ce problème](../ide/how-to-report-a-problem-with-visual-studio.md) à Visual Studio. Si vous avez besoin d’aide supplémentaire, consultez [Talk to Us](../ide/feedback-options.md) pour savoir comment contacter Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Quel est le message d’erreur détaillé?

Le `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` message est générique. Habituellement, un message plus spécifique est inclus dans la chaîne d’erreur et qui peut vous aider à identifier la cause du problème ou la recherche d’un correctif plus précis. Voici quelques-uns des messages d’erreur les plus courants qui sont annexés au message d’erreur principal :

- [Le débbuggeur ne peut pas se connecter à l’ordinateur distant. Le débogénaire n’a pas été en mesure de résoudre le nom d’ordinateur spécifié](#cannot_connect)
- [La demande de connexion a été rejetée par le débrouteur à distance](#rejected)
- [Accès invalide à l’emplacement de la mémoire](#invalid_access)
- [Il n’y a pas de serveur par le nom spécifié en cours d’exécution sur l’ordinateur distant](#no_server)
- [Le nom demandé était valide, mais aucune donnée du type demandé n’a été trouvée](#valid_name)
- [Le Visual Studio Remote Debugger sur l’ordinateur cible ne peut pas se connecter à cet ordinateur](#cant_connect_back)
- [Accès refusé](#access_denied)
- [Une erreur spécifique au paquet de sécurité s’est produite](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>Le débbuggeur ne peut pas se connecter à l’ordinateur distant. Le débogénaire n’a pas été en mesure de résoudre le nom d’ordinateur spécifié

Essayez d’effectuer les étapes suivantes :

1. Assurez-vous d’entrer un nom d’ordinateur valide et un numéro de port dans la boîte de dialogue **Attach to Process** ou dans les propriétés du projet (Pour définir les propriétés, voir ces [étapes](#server_incorrect)). Le nom de l’ordinateur doit être le format suivant :

    `computername:port`

    > [!NOTE]
    > Le numéro de port doit correspondre au [numéro de port du débbuggeur à distance](../debugger/remote-debugger-port-assignments.md), qui doit *fonctionner* sur la machine cible.

2. Si le nom de l’ordinateur ne fonctionne pas, essayez plutôt l’adresse IP et le numéro de port.

3. Assurez-vous que la version du débbuggeur à distance fonctionnant sur la machine cible correspond à votre version de Visual Studio. Pour obtenir la bonne version du débogage à distance, voir [Remote Debugging](../debugger/remote-debugging.md).

    > [!TIP]
    > Si vous vous attachez au processus et que vous vous connectez avec succès mais que vous ne voyez pas le processus que vous voulez, sélectionnez les **processus Afficher de la case à cocher de tous les utilisateurs.** Cela affichera les processus si vous êtes connecté sous un autre compte utilisateur.

4. Si ces étapes ne résolvent pas cette erreur, voir [La machine distante n’est pas accessible.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>La demande de connexion a été rejetée par le débrouteur à distance

Dans la boîte de dialogue **Attach to Process** ou dans les propriétés du projet, assurez-vous que le nom de l’ordinateur à distance et le numéro de port correspondent au nom et au numéro de port indiqués dans la fenêtre de débâcher à distance. Si incorrect, fixer et essayer à nouveau.

Si ces valeurs sont correctes et que le message mentionne le mode **d’authentification de Windows,** vérifiez que le débbuggeur à distance est dans le mode d’authentification correct **(Outils > Options**).

## <a name="the-connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>La connexion avec le critère d’évaluation à distance a été résiliée

Si vous débogagez une application Azure App Service, essayez d’utiliser la commande [Attach Debugger](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) de Cloud Explorer ou Server Explorer au lieu **d’attacher au processus**.

Si vous utilisez **Attach to Process** pour déboiffer :

1. Dans la boîte de dialogue **Attach to Process** ou dans les propriétés du projet, assurez-vous que le nom de l’ordinateur à distance et le numéro de port correspondent au nom et au numéro de port indiqués dans la fenêtre de débâcher à distance. Si incorrect, fixer et essayer à nouveau.

2. Vérifiez le journal d’application sur le serveur (Event Viewer sur Windows) pour obtenir des informations plus détaillées pour résoudre le problème.

3. Sinon, essayez de redémarrer Visual Studio avec les privilèges de l’administrateur, puis essayez à nouveau.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Accès invalide à l’emplacement de la mémoire

Une erreur interne s’est produite. Redémarrez Visual Studio et recommencez.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Il n’y a pas de serveur par le nom spécifié en cours d’exécution sur l’ordinateur distant

Visual Studio ne pouvait pas se connecter au débbugger à distance. Ce message peut se produire pour plusieurs raisons :

- Le débbuggeur à distance peut fonctionner sous un autre compte utilisateur. Voir [ces étapes](#user_accounts)

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu [ne bloque pas votre demande,](#firewall)surtout si vous utilisez un pare-feu tiers.

- La version de débogénaire à distance ne correspond pas à Visual Studio. Pour obtenir la bonne version du débogage à distance, voir [Remote Debugging](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>Le nom demandé était valide, mais aucune donnée du type demandé n’a été trouvée

L’ordinateur distant existe, mais Visual Studio ne pouvait pas se connecter au débbugger à distance. Ce message peut se produire pour plusieurs raisons :

- Un problème DNS empêche la connexion. Voir [ces étapes](#dns).

- Le débbuggeur à distance peut fonctionner sous un autre compte utilisateur. Suivez [ces étapes](#user_accounts).

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu [ne bloque pas votre demande,](#firewall)surtout si vous utilisez un pare-feu tiers.

- La version de débogénaire à distance ne correspond pas à Visual Studio. Pour obtenir la bonne version du débogage à distance, voir [Remote Debugging](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Le Visual Studio Remote Debugger sur l’ordinateur cible ne peut pas se connecter à cet ordinateur

Le débbuggeur à distance peut fonctionner sous un autre compte utilisateur. Dans le débbugger à distance, ouvrez **des outils > autorisations** pour ajouter l’utilisateur aux autorisations du débbuggeur à distance. Pour plus d’informations, voir [Le débbuggeur à distance fonctionne sous un compte utilisateur différent](#user_accounts).

Si le message d’erreur mentionne également un pare-feu, le pare-feu de la machine locale peut empêcher la communication de l’ordinateur distant vers Visual Studio. Voir [ces étapes](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a>Accès refusé

Vous pouvez voir cette erreur si vous essayez de déboiffer sur un ordinateur distant 64 bits à partir d’un ordinateur 32 bits (non pris en charge).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Une erreur spécifique au paquet de sécurité s’est produite

Il peut s’agir d’un problème hérité spécifique à Windows XP et Windows 7. Voir ces [informations](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causes et recommandations

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> L’ordinateur distant n’est pas accessible

Si vous ne pouvez pas vous connecter à l’aide du nom de l’ordinateur distant, essayez d’utiliser l’adresse IP à la place. Vous pouvez `ipconfig` utiliser dans une ligne de commande sur l’ordinateur distant pour obtenir l’adresse IPv4. Si vous utilisez un fichier HOSTS, vérifiez qu’il est configuré correctement.

Si cela échoue, vérifiez que l’ordinateur distant est accessible sur le réseau[(ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) la machine à distance). Le débogage à distance sur Internet n’est pas pris en charge, sauf dans certains scénarios Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>Le nom du serveur est incorrect ou le logiciel tiers interfère avec le débbuggeur à distance

Dans Visual Studio, regardez les propriétés du projet et assurez-vous que le nom du serveur est correct. Voir les sujets pour [C et Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) et CM [.](../debugger/remote-debugging-cpp.md#remote_cplusplus) Pour ASP.NET, ouvrez **Propriétés / Web / Serveurs** ou **Propriétés / Debug** selon votre type de projet.

> [!NOTE]
> Si vous vous attachez au processus, les paramètres distants des propriétés du projet ne sont pas utilisés.

Si le nom du serveur est correct, votre logiciel antivirus ou un pare-feu tiers peut bloquer le débbugger à distance. Lors de débogage localement, cela peut se produire parce que Visual Studio est une application 32 bits, de sorte qu’il utilise la version 64 bits du débbugger à distance pour déboguer des applications 64 bits. Les processus 32 bits et 64 bits communiquent à l’aide du réseau local à l’intérieur de l’ordinateur local. Aucun trafic réseau ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>Le débbuggeur à distance fonctionne sous un compte utilisateur différent

Le débbuggeur à distance n’acceptera, par défaut, que les connexions de l’utilisateur qui a lancé le débbugger à distance et les membres du groupe Des administrateurs. Les utilisateurs supplémentaires doivent recevoir explicitement des autorisations.

Pour résoudre ce problème, vous pouvez procéder de différentes façons :

- Ajoutez l’utilisateur Visual Studio aux autorisations du débbuggeur à distance (dans la fenêtre de débbuggeur à distance, choisissez **Des outils > autorisations).**

- Sur l’ordinateur distant, redémarrez le débbuggeur à distance sous le même compte utilisateur et mot de passe que vous utilisez sur l’ordinateur Visual Studio.

    > [!NOTE]
    > Si vous exécutez le débbugger à distance sur un serveur distant, cliquez à droite sur l’application Remote Debugger et choisissez **Run comme administrateur** (Ou, vous pouvez exécuter le débbugger à distance comme un service). Si vous ne l’exécutez pas sur un serveur distant, il suffit de le démarrer normalement.

- Vous pouvez démarrer le débogueur distant à partir de la ligne de commande à l’aide du paramètre **/allow \<nom_utilisateur>**  : `msvsmon /allow <username@computer>`.

- Alternativement, vous pouvez permettre à n’importe quel utilisateur de faire débogage à distance. Dans la fenêtre du débogueur distant, accédez à la boîte de dialogue **Outils > Options**. Quand vous sélectionnez   **Aucune authentification**, vous pouvez ensuite cocher **Permettre à tous les utilisateurs de déboguer**. Toutefois, vous ne devriez essayer cette option que si les autres options échouent, ou si vous êtes sur un réseau privé.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>Le pare-feu de la machine à distance ne permet pas les connexions entrantes au débbuggeur à distance
 Le pare-feu sur l’ordinateur Visual Studio et celui sur l’ordinateur distant doivent être configurés pour autoriser la communication entre Visual Studio et le débogueur distant. Pour plus d’informations sur les ports utilisés par le débogueur distant, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Pour plus d’informations sur la configuration du Pare-feu Windows, consultez [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La version du débogueur distant ne correspond pas à la version de Visual Studio
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Pour obtenir la bonne version du débogage à distance, voir [Remote Debugging](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Les ordinateurs locaux et distants utilisent des modes d’authentification différents
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez-vous que les deux ordinateurs utilisent le même mode d’authentification. Vous pouvez modifier le mode authentification. Dans la fenêtre de débocher à distance, rendez-vous sur la boîte de dialogue **Tools > Options.**

 Pour plus d’informations sur les modes d’authentification, consultez [Vue d’ensemble de l’authentification Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Un antivirus bloque les connexions
 L’antivirus Windows autorise les connexions au débogueur distant, mais certains antivirus tiers peuvent les bloquer. Consultez la documentation de votre antivirus pour savoir comment autoriser ces connexions.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La stratégie de sécurité réseau bloque la communication entre l’ordinateur distant et Visual Studio
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la politique de sécurité du réseau Windows, voir [paramètres de stratégie de sécurité](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Le réseau est trop occupé pour prendre en charge le débogage distant
 Dans ce cas, vous devrez peut-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.

## <a name="more-help"></a>Aide supplémentaire
 Pour obtenir plus d’aide de débbugger à distance, ouvrez la page d’aide du débbuggeur à distance **(Aide > Utilisation** dans le débbuggeur à distance).

## <a name="see-also"></a>Voir aussi
- [Débugging à distance](../debugger/remote-debugging.md)
