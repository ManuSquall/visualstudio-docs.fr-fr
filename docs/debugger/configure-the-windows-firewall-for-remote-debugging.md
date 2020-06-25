---
title: Configurer le pare-feu Windows pour le débogage distant | Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350691"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurer le pare-feu Windows pour le débogage distant

Sur un réseau protégé par le pare-feu Windows, le pare-feu doit être configuré pour autoriser le débogage distant. Visual Studio et les outils de débogage distant essaient d’ouvrir les ports de pare-feu corrects pendant l’installation ou le démarrage, mais vous devrez peut-être également ouvrir les ports ou autoriser les applications manuellement.

Cette rubrique explique comment configurer le pare-feu Windows pour activer le débogage à distance sur Windows 10, 8/8.1 et 7. et les ordinateurs Windows Server 2012 R2, 2012 et 2008 R2. Il n’est pas nécessaire que Visual Studio et l’ordinateur distant exécutent le même système d’exploitation. Par exemple, l’ordinateur Visual Studio peut exécuter Windows 10 et l’ordinateur distant peut exécuter Windows Server 2012 R2.

>[!NOTE]
>Les instructions de configuration du pare-feu Windows diffèrent légèrement en fonction des systèmes d’exploitation et des versions antérieures de Windows. Les paramètres Windows 8/8.1, Windows 10 et Windows Server 2012 utilisent le mot *application*, tandis que Windows 7 et windows Server 2008 utilisent le *programme*Word.

## <a name="configure-ports-for-remote-debugging"></a>Configurer des ports pour le débogage distant

Visual Studio et le débogueur distant essaient d’ouvrir les ports corrects pendant l’installation ou le démarrage. Toutefois, dans certains scénarios, tels qu’un pare-feu tiers, vous devrez peut-être ouvrir les ports manuellement.

**Pour ouvrir un port :**

1. Dans le menu **Démarrer** de Windows, recherchez et ouvrez **pare-feu Windows avec fonctions avancées de sécurité**. Dans Windows 10, il s’agit du **pare-feu Windows Defender avec fonctions avancées de sécurité**.

1. Pour un nouveau port entrant, sélectionnez **règles de trafic** entrant, puis sélectionnez **nouvelle règle**. Pour une règle sortante, sélectionnez **règles de trafic** sortant à la place.

1. Dans l' **Assistant Nouvelle règle de trafic entrant**, sélectionnez **port**, puis cliquez sur **suivant**.

1. Sélectionnez **TCP** ou **UDP**, selon le numéro de port des tables suivantes.

1. Sous **ports locaux spécifiques**, entrez un numéro de port parmi les tables suivantes, puis sélectionnez **suivant**.

1. Sélectionnez **autoriser la connexion**, puis cliquez sur **suivant**.

1. Sélectionnez un ou plusieurs types de réseau à activer, y compris le type de réseau pour la connexion à distance, puis sélectionnez **suivant**.

1. Ajoutez un nom pour la règle (par exemple, **msvsmon**, **IIS**ou **Web Deploy**), puis sélectionnez **Terminer**.

   La nouvelle règle doit apparaître et être sélectionnée dans la liste **règles** de trafic entrant ou **règles de trafic sortant** .

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports sur l’ordinateur distant qui permettent le débogage distant

Pour le débogage distant, les ports suivants doivent être ouverts sur l’ordinateur distant :

::: moniker range="vs-2017"

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|4022|Entrant|TCP|Pour VS 2017. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez [affectations de port du débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Entrant|TCP|Pour VS 2017. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Ce port est utilisé uniquement pour déboguer à distance un processus 32 bits à partir d’une version 64 bits du débogueur distant. Pour plus d’informations, consultez [affectations de port du débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Sortant|UDP|Facultatif Requis pour la détection du débogueur distant.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|4024|Entrant|TCP|Pour VS 2019. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez [affectations de port du débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Entrant|TCP|Pour VS 2019. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Ce port est utilisé uniquement pour déboguer à distance un processus 32 bits à partir d’une version 64 bits du débogueur distant. Pour plus d’informations, consultez [affectations de port du débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Sortant|UDP|Facultatif Requis pour la détection du débogueur distant.|

::: moniker-end

Si vous sélectionnez **utiliser le mode de compatibilité managé** dans **Outils**  >  **options**  >  de**débogage**, ouvrez ces ports supplémentaires du débogueur distant. Le mode de compatibilité managé du débogueur active une version héritée de Visual Studio 2010 du débogueur.

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|135, 139, 445|Sortant|TCP|Obligatoire.|
|137, 138|Sortant|UDP|Obligatoire.|

Si votre stratégie de domaine nécessite que la communication réseau soit effectuée via IPSec, vous devez ouvrir des ports supplémentaires sur les ordinateurs Visual Studio et distants. Pour déboguer sur un serveur Web IIS distant, ouvrez le port 80 sur l’ordinateur distant.

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|500, 4500|Sortant|UDP|Requis si votre stratégie de domaine nécessite que la communication réseau soit effectuée via IPSec.|
|80|Sortant|TCP|Requis pour le débogage du serveur web.|

Pour autoriser des applications spécifiques par le biais du pare-feu Windows, consultez [configurer le débogage à distance via le pare-feu Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurer le débogage à distance via le pare-feu Windows

Vous pouvez installer les outils de débogage distant sur l’ordinateur distant ou les exécuter à partir d’un dossier partagé. Dans les deux cas, le pare-feu de l’ordinateur distant doit être configuré correctement.

Sur un ordinateur distant, les outils de débogage distant se trouvent dans :

*\<Visual Studio installation directory\>\\\\ \\ Débogueur distant IDE Common7\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Autoriser et configurer le débogueur distant par le biais du pare-feu Windows

1. Dans le menu **Démarrer** de Windows, recherchez et ouvrez le pare-feu **Windows**ou le **pare-feu Windows Defender**.

1. Sélectionnez **autoriser une application via le pare-feu Windows**.

1. Si le **débogueur distant** ou le **débogueur distant Visual Studio** ne s’affiche pas sous **applications et fonctionnalités autorisées**, sélectionnez **modifier les paramètres**, puis sélectionnez **autoriser une autre application**.

1. Si l’application du débogueur distant n’est toujours pas listée dans la boîte de dialogue **Ajouter une application** , sélectionnez **Parcourir**, puis accédez à * \<Visual Studio installation directory\> \\ Common7 \\ IDE \\ Remote Debugger \\ \<x86*, *x64*, or *Appx*\> , en fonction de l’architecture appropriée pour votre application. Sélectionnez *msvsmon.exe*, puis **Ajouter**.

1. Dans la liste des **applications** , sélectionnez le **débogueur distant** que vous venez d’ajouter. Sélectionnez **types de réseau**, puis sélectionnez un ou plusieurs types de réseau, y compris le type de réseau pour la connexion à distance.

1. Sélectionnez **Ajouter**, puis **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Résoudre les problèmes liés à la connexion de débogage distant

Si vous ne pouvez pas attacher votre application avec le débogueur distant, assurez-vous que les ports de pare-feu de débogage distant, les protocoles, les types de réseau et les paramètres d’application sont tous corrects.

- Dans le menu **Démarrer** de Windows, recherchez et ouvrez le **pare-feu Windows**, puis sélectionnez **autoriser une application via le pare-feu Windows**. Vérifiez que **débogueur distant** ou **débogueur distant Visual Studio** apparaît dans la liste **applications et fonctionnalités autorisées** avec une case à cocher activée et que les types de réseau corrects sont sélectionnés. Si ce n’est pas le cas, [Ajoutez les applications et les paramètres appropriés](#configure-remote-debugging-through-windows-firewall).

- Dans le menu **Démarrer** de Windows, recherchez et ouvrez **pare-feu Windows avec fonctions avancées de sécurité**. Assurez-vous que **débogueur distant** ou **débogueur distant Visual Studio** apparaît sous **règles de trafic entrant** (et éventuellement les **règles de trafic sortant**) avec une icône de coche verte et que tous les paramètres sont corrects.

  - Pour afficher ou modifier les paramètres de règle, cliquez avec le bouton droit sur l’application du **débogueur distant** dans la liste et sélectionnez **Propriétés**. Utilisez les onglets **Propriétés** pour activer ou désactiver la règle, ou modifier les numéros de port, les protocoles ou les types de réseau.
  - Si l’application du débogueur distant n’apparaît pas dans la liste des règles, [Ajoutez et configurez les ports appropriés](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Voir aussi

- [Débogage distant](../debugger/remote-debugging.md)
- [Affectations de port du débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md)
