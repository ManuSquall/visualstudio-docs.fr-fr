---
title: Impossible de se connecter à Microsoft Visual Studio Remote Debugging Monitor | Documents Microsoft
ms.custom: ''
ms.date: 08/24/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5b7af9c41aac0531a9af014a49e9e0a1e71763d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Impossible de se connecter à l’ordinateur Microsoft Visual Studio Remote Debugging Monitor
Ce message peut survenir, car le remote debugging monitor n’est pas correctement configuré sur l’ordinateur distant ou l’ordinateur distant est inaccessible en raison de problèmes réseau ou de la présence d’un pare-feu.
  
> [!IMPORTANT]
>  Si vous pensez que vous avez reçu ce message en raison d’un bogue de produit, veuillez [signaler ce problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) à Visual Studio. Si vous avez besoin d’aide supplémentaire, consultez [Talk to Us](../ide/talk-to-us.md) pour savoir comment contacter Microsoft.

## <a name="specificerrors"></a>Qu’est le message d’erreur détaillé ?

Le `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` message est générique. En règle générale, un message plus spécifique est inclus dans la chaîne d’erreur et qui peuvent vous aider à identifier la cause du problème ou de recherche pour une solution plus exacte. Voici quelques exemples de messages d’erreur les plus courants sont ajoutées au message d’erreur principal :

- [Le débogueur ne peut pas se connecter à l’ordinateur distant. Le débogueur n’a pas pu résoudre le nom de l’ordinateur spécifié](#cannot_connect)
- [Demande de connexion a été rejetée par le débogueur distant](#rejected)
- [Accès non valide à l’emplacement de mémoire](#invalid_access)
- [Il n’existe aucun serveur portant le nom spécifié est en cours d’exécution sur l’ordinateur distant](#no_server)
- [Le nom demandé était valide, mais aucune donnée du type demandé a été trouvée.](#valid_name)
- [Le débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur](#cant_connect_back)
- [Accès refusé](#access_denied)
- [Une erreur spécifique de package de sécurité s’est produite](#security_package)

## <a name="cannot_connect"></a> Le débogueur ne peut pas se connecter à l’ordinateur distant. Le débogueur n’a pas pu résoudre le nom de l’ordinateur spécifié

Essayez les étapes suivantes :

1. Assurez-vous que vous entrez un nom d’ordinateur valide et numéro du port dans le **attacher au processus** boîte de dialogue ou dans les propriétés du projet (pour définir les propriétés, consultez [suit](#server_incorrect)). Le nom d’ordinateur doit être au format suivant :

    `computername:port`

    > [!NOTE]
    > Le numéro de port doit correspondre à la [numéro de port du débogueur distant](../debugger/remote-debugger-port-assignments.md), qui *doit être en cours d’exécution* sur l’ordinateur cible.

2. Si le nom d’ordinateur ne fonctionne pas, essayez de l’adresse IP et numéro de port à la place.

3. Assurez-vous que la version du débogueur distant en cours d’exécution sur l’ordinateur cible correspond à votre version de Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

    > [!TIP]
    > Si vous attachez au processus et vous connectez correctement mais que vous ne voyez pas le processus que vous souhaitez, sélectionnez le **afficher les processus de tous les utilisateurs case à cocher**. Cette opération affiche les processus si vous êtes connecté sous un compte d’utilisateur différent.

4. Si ces étapes ne résolvent pas cette erreur, consultez [l’ordinateur distant n’est pas accessible](#dns).

## <a name="rejected"></a> Demande de connexion a été rejetée par le débogueur distant

Dans le **attacher au processus** boîte de dialogue zone, ou dans les propriétés du projet, assurez-vous que le nom de l’ordinateur distant et le numéro de port correspond au nom et numéro de port indiqué dans la fenêtre du débogueur distant. Si elle est incorrecte, corrigez et réessayez.

Si ces valeurs sont correctes et que le message mentionne **l’authentification Windows** mode, vérifiez que le débogueur distant se trouve dans le mode d’authentification approprié (**Outils > Options**).

## <a name="invalid_access"></a> Accès non valide à l’emplacement de mémoire

Une erreur interne s’est produite. Redémarrez Visual Studio et réessayez.

## <a name="no_server"></a> Il n’existe aucun serveur portant le nom spécifié est en cours d’exécution sur l’ordinateur distant

Visual Studio n’a pas pu se connecter au débogueur distant. Ce message peut se produire pour plusieurs raisons :

- Le débogueur distant peut être exécuté sous un compte d’utilisateur différent. Consultez [ces étapes.](#user_accounts)

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu [ne pas bloque votre demande](#firewall), surtout si vous utilisez un pare-feu tiers.

- La version du débogueur distant ne correspond pas à Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md)


## <a name="#valid_name"></a> Le nom demandé était valide, mais aucune donnée du type demandé a été trouvée.

L’ordinateur distant existe, mais Visual Studio n’a pas pu se connecter au débogueur distant. Ce message peut se produire pour plusieurs raisons :

- Un problème DNS empêche la connexion. Consultez [suit](#dns).

- Le débogueur distant peut être exécuté sous un compte d’utilisateur différent. Suivez [suit](#user_accounts).

- Le port est bloqué sur le pare-feu. Assurez-vous que le pare-feu [ne pas bloque votre demande](#firewall), surtout si vous utilisez un pare-feu tiers.

- La version du débogueur distant ne correspond pas à Visual Studio. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Le débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur

Le débogueur distant peut être exécuté sous un compte d’utilisateur différent. Dans le débogueur distant, ouvrez **Outils > autorisations** pour ajouter l’utilisateur aux autorisations du débogueur distant. Pour plus d’informations, consultez [le débogueur distant s’exécute sous un compte d’utilisateur différent](#user_accounts).

Si le message d’erreur mentionne également un pare-feu, le pare-feu sur l’ordinateur local peut empêcher la communication à partir de l’ordinateur distant vers Visual Studio. Consultez [suit](#firewall).

## <a name="access_denied"></a> Accès refusé

Vous pouvez voir cette erreur si vous essayez de déboguer sur un ordinateur distant 64 bits à partir d’un ordinateur 32 bits (non pris en charge).

## <a name="security_package"></a> Une erreur spécifique de package de sécurité s’est produite

Cela peut être un problème hérité spécifique à Windows XP et Windows 7. Consultez ce [informations](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Les causes et les recommandations

### <a name="dns"></a> L’ordinateur distant n’est pas accessible 

Si vous ne pouvez pas vous connecter en utilisant le nom de l’ordinateur distant, essayez d’utiliser l’adresse IP à la place. Vous pouvez utiliser `ipconfig` dans une ligne de commande sur l’ordinateur distant pour obtenir l’adresse IPv4. Si vous utilisez un fichier HOSTS, vérifiez qu’il est correctement configuré.

En cas d’échec, vérifiez que l’ordinateur distant est accessible sur le réseau ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx) l’ordinateur distant). Débogage à distance via Internet n’est pas pris en charge, sauf dans certains scénarios Microsoft Azure.
  
### <a name="server_incorrect"></a> Le nom du serveur est incorrect ou les logiciels tiers interfère avec le débogueur distant

Dans Visual Studio, examinez les propriétés du projet et assurez-vous que le nom du serveur est correct. Consultez les rubriques relatives aux [c# et Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) et [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Pour ASP.NET, ouvrez **propriétés / Web / serveurs** ou **propriétés /Debug** en fonction de votre type de projet.

> [!NOTE]
> Si vous attachez au processus, les paramètres à distance dans les propriétés du projet ne sont pas utilisés.

Si le nom du serveur est correct, votre logiciel antivirus ou un pare-feu tiers bloque le débogueur distant. Lorsque vous déboguez localement, cela peut se produire si Visual Studio est une application 32 bits, de sorte qu’elle utilise la version 64 bits du débogueur distant pour déboguer des applications 64 bits. Les processus 32 bits et 64 bits communiquent à l’aide du réseau local au sein de l’ordinateur local. Aucun trafic réseau ne quitte l’ordinateur, mais il peut arriver que des logiciels de sécurité tiers bloquent la communication.

### <a name="user_accounts"></a> Le débogueur distant s’exécute sous un compte d’utilisateur différent 

Le débogueur distant, par défaut, accepte uniquement les connexions à partir de l’utilisateur qui a lancé le débogueur distant et les membres du groupe Administrateurs. Des utilisateurs supplémentaires doivent être explicitement des autorisations. 
 
Pour résoudre ce problème, vous pouvez procéder de différentes façons :  

-   Ajouter l’utilisateur de Visual Studio pour les autorisations du débogueur distant (dans la fenêtre du débogueur distant, choisissez **Outils > autorisations**).

-   Sur l’ordinateur distant, redémarrez le débogueur distant sous le même compte d’utilisateur et un mot de passe que vous utilisez sur l’ordinateur Visual Studio.

    > [!NOTE]
    > Si vous exécutez le débogueur distant sur un serveur distant, cliquez sur l’application du débogueur distant et choisissez **exécuter en tant qu’administrateur** (ou, vous pouvez exécuter le débogueur distant en tant que service). Si vous n’exécutez pas sur un serveur distant, juste le démarrer normalement.
  
-   Vous pouvez démarrer le débogueur distant à partir de la ligne de commande avec le **/ autoriser \<nom d’utilisateur >** paramètre : `msvsmon /allow <username@computer>`. 
  
-   Vous pouvez également autoriser tout utilisateur d’effectuer un débogage distant. Dans la fenêtre du débogueur distant, accédez à la **Outils > Options** boîte de dialogue. Quand vous sélectionnez   **Aucune authentification**, vous pouvez ensuite cocher **Permettre à tous les utilisateurs de déboguer**. Toutefois, vous devez essayer cette option uniquement si les autres options ont échoué, ou si vous êtes sur un réseau privé.

### <a name="firewall"></a> Le pare-feu sur l’ordinateur distant n’autorise pas les connexions entrantes au débogueur distant  
 Le pare-feu sur l’ordinateur Visual Studio et celui sur l’ordinateur distant doivent être configurés pour autoriser la communication entre Visual Studio et le débogueur distant. Pour plus d’informations sur les ports utilisés par le débogueur distant, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Pour plus d’informations sur la configuration du Pare-feu Windows, consultez [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La version du débogueur distant ne correspond pas à la version de Visual Studio  
 La version de Visual Studio que vous exécutez localement doit correspondre à la version de Remote Debugging Monitor qui s’exécute sur l’ordinateur distant. Pour résoudre ce problème, téléchargez et installez la version correspondante de Remote Debugging Monitor. Pour obtenir la version correcte du débogueur distant, consultez [débogage distant](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Les ordinateurs locaux et distants utilisent des modes d’authentification différents  
 Les ordinateurs locaux et distants doivent utiliser le même mode d’authentification. Pour résoudre ce problème, assurez-vous que les deux ordinateurs utilisent le même mode d’authentification. Vous pouvez modifier le mode d’authentification. Dans la fenêtre du débogueur distant, accédez à la **Outils > Options** boîte de dialogue.
  
 Pour plus d’informations sur les modes d’authentification, consultez [Vue d’ensemble de l’authentification Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Un antivirus bloque les connexions  
 L’antivirus Windows autorise les connexions au débogueur distant, mais certains antivirus tiers peuvent les bloquer. Consultez la documentation de votre antivirus pour savoir comment autoriser ces connexions.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La stratégie de sécurité réseau bloque la communication entre l’ordinateur distant et Visual Studio  
 Passez en revue la sécurité de votre réseau pour vous assurer qu’elle ne bloque pas les communications. Pour plus d’informations sur la stratégie de sécurité réseau de Windows, consultez [les paramètres de stratégie de sécurité](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Le réseau est trop occupé pour prendre en charge le débogage distant  
 Dans ce cas, vous devrez peut-être procéder au débogage distant ultérieurement ou replanifier le travail sur le réseau à une heure différente.  
  
## <a name="more-help"></a>Aide supplémentaire  
 Pour obtenir de l’aide de débogueur distant, ouvrez la page d’aide du débogueur distant (**aide > utilisation** dans le débogueur distant).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)