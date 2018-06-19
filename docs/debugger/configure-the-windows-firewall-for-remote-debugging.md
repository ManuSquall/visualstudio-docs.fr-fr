---
title: Configurer le pare-feu Windows pour le débogage à distance | Documents Microsoft
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9fdd6db229bf1aa6f607e096715ea485ec5c5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465198"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Configurer le Pare-feu Windows pour le débogage distant
Cette rubrique explique comment configurer le pare-feu pour activer le débogage distant sur des ordinateurs qui exécutent les systèmes d’exploitation suivants :  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 Si le réseau sur lequel vous effectuez un débogage n’est pas protégé par un pare-feu, cette configuration est inutile. Dans le cas contraire, il est nécessaire d’apporter des modifications à la configuration du pare-feu pour l’ordinateur qui héberge Visual Studio et l’ordinateur distant qui doit être débogué.  
  
 **IPSec** Si votre réseau nécessite que la communication soit effectuée à l’aide d’IPSec, vous devez ouvrir des ports supplémentaires sur l’ordinateur hôte Visual Studio et l’ordinateur distant.  
  
 **Serveur web** Si vous déboguez un serveur web distant, vous devez ouvrir un port supplémentaire sur l’ordinateur distant. (Pour IIS, le port 80 doit être ouvert).  
  
 Notez que les deux ordinateurs n’ont pas à exécuter le même système d’exploitation. Par exemple, l’ordinateur Visual Studio peut exécuter Windows 10 et l’ordinateur distant peut exécuter Windows Server 2012 R2.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports sur l’ordinateur distant qui permettent le débogage distant  
  
|||||  
|-|-|-|-|  
|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|   
|4022|entrant|TCP|Pour VS 2017. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez [Visual Studio affectations de Port débogueur distant](../debugger/remote-debugger-port-assignments.md).|  
|4023|entrant|TCP|Pour VS 2017. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. (Uniquement utilisés à distance déboguer un processus 32 bits à partir de la version 64 bits du débogueur distant.) Pour plus d’informations, consultez [Visual Studio affectations de Port débogueur distant](../debugger/remote-debugger-port-assignments.md).| 
|3702|Sortant|UDP|(Facultatif) Requis pour la détection du débogueur distant.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Comment configurer des ports dans le Pare-feu Windows  

Lorsque vous installez Visual Studio ou le débogueur distant, le logiciel tente d’ouvrir les ports appropriés. Toutefois, dans certains scénarios (par exemple, à l’aide d’un pare-feu tiers), vous devrez peut-être ouvrir un port manuellement. Si vous devez vérifier que les ports sont ouverts, consultez [dépannage](#troubleshooting). Des instructions relatives à l’ouverture d’un port peuvent être différents sur les versions antérieures de Windows.

Pour ouvrir un port :
  
1. Ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant > nouvelle règle > Port**, puis cliquez sur **suivant**. (Pour les règles sortantes, choisissez **règles de trafic sortant** à la place.)

3. Choisissez **TCP** ou **UDP**, selon le numéro de port.

4. Sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**.

5. Cliquez sur **Allow the Connection** , puis sur **Suivant**.

6. Sélectionnez un ou plusieurs types de réseau à activer pour le port, puis cliquez sur **suivant**.

    Les types que vous sélectionnez doivent inclure le réseau auquel l’ordinateur distant est connecté.
7. Ajoutez le nom (par exemple, **msvsmon**, **IIS**, ou **Web Deploy**) pour la règle et cliquez sur **Terminer**.

    Vous devez voir votre nouvelle règle dans la liste des règles de trafic entrant et les règles de trafic sortant.

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous avez des difficultés à attacher à votre application avec le débogueur distant, vous devrez peut-être vérifier que les ports appropriés sont ouverts.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Vérifiez que les ports sont ouverts dans le pare-feu Windows sur l’ordinateur Visual Studio  
 Les instructions pour configurer le Pare-feu Windows diffèrent légèrement en fonction des systèmes d’exploitation. Sur Windows 8/8.1, Windows 10 et Windows Server 2012, le mot **application** est utilisé ; sur Windows 7 ou Windows Server 2008, le mot **programme** est utilisé ;  Dans les étapes suivantes, nous allons utiliser le mot **application**.  
  
1.  Ouvrez la page Pare-feu Windows. (Dans la zone de recherche du menu **Démarrer** , tapez **Pare-feu Windows**.)  
  
2.  Cliquez sur **Autoriser une application ou une fonctionnalité via le Pare-feu Windows**.  
  
3.  Dans la liste **Applications et fonctionnalités autorisées** , recherchez **Détection du débogueur distant de Visual Studio**. Si l’option est répertoriée, assurez-vous qu’elle est sélectionnée et qu’un ou que plusieurs types de réseau sont également sélectionnés.  
  
4.  Si l’option **Détection du débogueur distant de Visual Studio** n’est pas répertoriée, cliquez sur **Autoriser une autre application**. Si vous ne retrouvez dans le **ajouter une application** fenêtre, cliquez sur **Parcourir** et accédez à  **\<répertoire d’installation de Visual Studio > \Common7\IDE\Remote Debugger**. Recherchez le dossier approprié pour l’application (x86, x64, Appx), puis sélectionnez **msvsmon.exe**. Cliquez ensuite sur **Ajouter**.  
  
5.  Dans le **autorisée des applications et fonctionnalités** liste, sélectionnez **Visual Studio Remote Debugger**. Cochez un ou plusieurs types de réseau (**Domaine, Domestique/entreprise (privé), Public**) avec lesquels vous souhaitez que Remote Debugging Monitor communique. Les types doivent inclure le réseau auquel l’ordinateur Visual Studio est connecté. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Vérifiez que les ports sont ouverts dans le pare-feu Windows sur l’ordinateur distant  
 Les composants de débogage distant peuvent être installés sur l’ordinateur distant ou exécutés à partir d’un répertoire partagé. Le pare-feu de l’ordinateur distant doit être configuré dans les deux cas. Les composants de débogage distants sont situés dans :  
  
 **\<Répertoire d’installation de Visual Studio > \Common7\IDE\Remote Debugger**  
  
 Les instructions pour configurer le Pare-feu Windows diffèrent légèrement en fonction des systèmes d’exploitation. Sur Windows 8/8.1, Windows 10 et Windows Server 2012, le mot **application** est utilisé ; sur Windows 7 ou Windows Server 2008, le mot **programme** est utilisé ;  Dans les étapes suivantes, nous allons utiliser le mot **application**.  
  
1.  Ouvrez la page Pare-feu Windows. (Dans la zone de recherche du menu **Démarrer** , tapez **Pare-feu Windows**.)  
  
2.  Cliquez sur **Autoriser une application ou une fonctionnalité via le Pare-feu Windows**.  
  
3.  Dans le **autorisée des applications et fonctionnalités** liste, recherchez **Visual Studio Remote Debugger**. Si l’option est répertoriée, assurez-vous qu’elle est sélectionnée et qu’un ou que plusieurs types de réseau sont également sélectionnés.  
  
4.  Si **Visual Studio Remote Debugger** est ne pas répertorié, cliquez sur **autoriser une autre application**. Si vous ne retrouvez dans le **ajouter une fenêtre de l’application**, cliquez sur **Parcourir** et accédez à  **\<répertoire d’installation de Visual Studio > \Common7\IDE\Remote Debugger**. Recherchez le dossier approprié pour l’application (x86, x64, Appx), puis sélectionnez **msvsmon.exe**. Cliquez ensuite sur **Ajouter**.  
  
5.  Dans le **autorisés applications** liste, sélectionnez **Visual Studio Remote Debugger**. Cochez un ou plusieurs types de réseau (**Domaine, Domestique/entreprise (privé), Public**) avec lesquels vous souhaitez que Remote Debugging Monitor communique. Les types doivent inclure le réseau auquel l’ordinateur Visual Studio est connecté. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Mode de compatibilité managé ou natif) Ouvrir des ports supplémentaires sur l’ordinateur distant

Si vous utilisez le mode de compatibilité pour le débogueur (**Outils > Options > débogage**), des ports supplémentaires seront doivent être ouverts. Mode de compatibilité permet à une version héritée du débogueur et des ports différents sont requis.

> [!NOTE]
> L’ancienne version du débogueur est le débogueur Visual Studio 2010.
  
|||||  
|-|-|-|-|  
|**Ports**|**Entrant/sortant**|**Protocole**|**Description**|  
|135, 139, 445|Sortant|TCP|Requis.|  
|137, 138|Sortant|UDP|Obligatoire.|  
|500, 4500|Sortant|UDP|Requis si votre stratégie de domaine nécessite que la communication réseau soit effectuée via IPSec.|  
|80|Sortant|TCP|Requis pour le débogage du serveur web.|
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)