---
title: Configurer le pare-feu de Windows pour le débogage à distance | Microsoft Docs
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff64735e1711a18bd7c55c6e052fa8579bd12e16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563719"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurer le pare-feu de Windows pour le débogage distant

Sur un réseau protégé par le pare-feu Windows, le pare-feu doit être configuré pour autoriser le débogage à distance. Visual Studio et les outils de débogage à distance essaient d’ouvrir les ports corrects du pare-feu durant l’installation ou de démarrage, mais vous devrez peut-être également ouvrir des ports ou autoriser les applications manuellement.

Cette rubrique explique comment configurer le pare-feu Windows pour activer le débogage à distance sur Windows 10, 8/8.1 et 7 ; et les ordinateurs Windows Server 2012 R2, 2012 et 2008 R2. L’ordinateur distant et Visual Studio n’êtes pas obligé d’exécuter le même système d’exploitation. Par exemple, l’ordinateur Visual Studio peut exécuter Windows 10 et l’ordinateur distant peut exécuter Windows Server 2012 R2.

>[!NOTE]
>Les instructions pour configurer le pare-feu Windows diffèrent légèrement sur différents systèmes d’exploitation et pour les versions antérieures de Windows. Paramètres de Windows 8/8.1, Windows 10 et Windows Server 2012 utilisent le mot *application*, tandis que Windows 7 et Windows Server 2008 utilisent le mot *programme*.

## <a name="configure-ports-for-remote-debugging"></a>Configurer des ports pour le débogage distant

Visual Studio et le débogueur distant essaient d’ouvrir les ports appropriés pendant l’installation ou de démarrage. Toutefois, dans certains scénarios, tel qu’un pare-feu tiers, vous devrez peut-être ouvrir des ports manuellement.

**Pour ouvrir un port :**

1. Dans Windows **Démarrer** menu, recherchez et ouvrez **pare-feu Windows avec fonctions avancées de sécurité**. Dans Windows 10, il s’agit de **pare-feu Windows Defender avec fonctions avancées de sécurité**.

1. Pour un nouveau port entrant, sélectionnez **règles de trafic entrant** , puis sélectionnez **nouvelle règle**. Pour une règle sortante, sélectionnez **règles de trafic sortant** à la place.

1. Dans le **Assistant Nouvelle règle de trafic entrant**, sélectionnez **Port**, puis sélectionnez **suivant**.

1. Sélectionnez **TCP** ou **UDP**, selon le numéro de port à partir des tables suivantes.

1. Sous **ports locaux spécifiques**, entrez un numéro de port à partir des tables suivantes, puis sélectionnez **suivant**.

1. Sélectionnez **autoriser la connexion**, puis sélectionnez **suivant**.

1. Sélectionnez un ou plusieurs types de réseau à activer, y compris le type de réseau pour la connexion à distance, puis **suivant**.

1. Ajouter un nom pour la règle (par exemple, **msvsmon**, **IIS**, ou **Web Deploy**), puis sélectionnez **Terminer**.

   La nouvelle règle doit apparaître et être sélectionnée dans le **règles de trafic entrant** ou **règles de trafic sortant** liste.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports sur l’ordinateur distant qui permettent le débogage distant

Pour le débogage distant, les ports suivants doivent être ouverts sur l’ordinateur distant :

::: moniker range="vs-2017"

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|4022|Entrant|TCP|Pour VS 2017. Le port numéro s’incrémente de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez [Affectations de port du débogueur distant de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Entrant|TCP|Pour VS 2017. Le port numéro s’incrémente de 2 pour chaque version de Visual Studio. Ce port est uniquement utilisé à distance déboguer un processus 32 bits à partir d’une version 64 bits du débogueur distant. Pour plus d’informations, consultez [Affectations de port du débogueur distant de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Sortant|UDP|(Facultatif) Requis pour la détection du débogueur distant.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|4024|Entrant|TCP|Pour VS 2019. Le port numéro s’incrémente de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez [Affectations de port du débogueur distant de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Entrant|TCP|Pour VS 2019. Le port numéro s’incrémente de 2 pour chaque version de Visual Studio. Ce port est uniquement utilisé à distance déboguer un processus 32 bits à partir d’une version 64 bits du débogueur distant. Pour plus d’informations, consultez [Affectations de port du débogueur distant de Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Sortant|UDP|(Facultatif) Requis pour la détection du débogueur distant.|

::: moniker-end

Si vous sélectionnez **utiliser le Mode compatibilité managé** sous **outils** > **Options** > **débogage**, ouvrez ces ports supplémentaires débogueur distant. Mode de compatibilité de débogueur managé permet un hérité, la version de Visual Studio 2010 du débogueur.

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|135, 139, 445|Sortant|TCP|Requis.|
|137, 138|Sortant|UDP|Obligatoire.|

Si votre stratégie de domaine nécessite la communication réseau soit effectuée via IPSec, vous devez ouvrir des ports supplémentaires sur Visual Studio et les ordinateurs distants. Pour déboguer sur un serveur de web IIS distant, ouvrez le port 80 sur l’ordinateur distant.

|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|
|-|-|-|-|
|500, 4500|Sortant|UDP|Requis si votre stratégie de domaine nécessite que la communication réseau soit effectuée via IPSec.|
|80|Sortant|TCP|Requis pour le débogage du serveur web.|

Pour permettre à des applications spécifiques via le pare-feu Windows, consultez [configurer le débogage à distance via le pare-feu de Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurer le débogage à distance via le pare-feu de Windows

Vous pouvez installer les outils de débogage à distance sur l’ordinateur distant, ou les exécuter à partir d’un dossier partagé. Dans les deux cas, le pare-feu de l’ordinateur distant doit être configuré correctement.

Sur un ordinateur distant, les outils de débogage distants sont dans :

*\<Répertoire d’installation de Visual Studio\>\\Common7\\IDE\\débogueur distant\\\<x86*, *x64*, ou  *AppX*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Autoriser et configurer le débogueur distant via le pare-feu de Windows

1. Dans Windows **Démarrer** menu, recherchez et ouvrez **Windows Firewall**, ou **pare-feu Windows Defender**.

1. Sélectionnez **permettre à une application via le pare-feu de Windows**.

1. Si **débogueur distant** ou **débogueur distant Visual Studio** n’apparaît pas sous **applications et fonctionnalités autorisées**, sélectionnez **modifier les paramètres**, puis sélectionnez **autoriser une autre application**.

1. Si l’application débogueur distant n’est pas toujours répertoriée dans le **ajouter une application** boîte de dialogue, sélectionnez **Parcourir**et accédez à  *\<répertoire d’installation de Visual Studio\> \\Common7\\IDE\\débogueur distant\\\<x86*, *x64*, ou *Appx* \> , en fonction de l’architecture appropriée pour votre application. Sélectionnez *msvsmon.exe*, puis sélectionnez **ajouter**.

1. Dans le **applications** liste, sélectionnez le **débogueur distant** que vous venez d’ajouter. Sélectionnez **types de réseau**, puis sélectionnez un ou plusieurs types de réseau, y compris le type de réseau pour la connexion à distance.

1. Sélectionnez **ajouter**, puis sélectionnez **OK**.

## <a name="troubleshooting"></a>Résoudre les problèmes de la connexion de débogage à distance

Si vous ne pouvez pas attacher à votre application avec le débogueur distant, assurez-vous que les ports du pare-feu de débogage à distance, protocoles, les types de réseau et les paramètres d’application sont corrects.

- Dans le Windows **Démarrer** menu, recherchez et ouvrez **Windows Firewall**, puis sélectionnez **permettre à une application via le pare-feu de Windows**. Assurez-vous que **débogueur distant** ou **débogueur distant Visual Studio** s’affiche dans le **applications et fonctionnalités autorisées** liste avec une case à cocher activée et les types de réseau corrects sont sélectionné. Si ce n’est pas le cas, [ajouter les applications correctes et les paramètres](#configure-remote-debugging-through-windows-firewall).

- Dans le Windows **Démarrer** menu, recherchez et ouvrez **pare-feu Windows avec fonctions avancées de sécurité**. Assurez-vous que **débogueur distant** ou **débogueur distant Visual Studio** apparaît sous **règles de trafic entrant** (et éventuellement, **règles de trafic sortant**) avec une coche verte et que tous les paramètres sont corrects.

  - Pour afficher ou modifier les paramètres de règle, cliquez sur le **débogueur distant** application dans la liste et sélectionnez **propriétés**. Utilisez le **propriétés** onglets pour activer ou désactiver la règle ou modifier le port nombres, des protocoles ou types de réseau.
  - Si l’application débogueur distant n’apparaît pas dans la liste des règles, [ajouter et configurer les ports corrects](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Voir aussi

- [Débogage distant](../debugger/remote-debugging.md)
- [Affectations de port débogueur distant Visual Studio](../debugger/remote-debugger-port-assignments.md)
