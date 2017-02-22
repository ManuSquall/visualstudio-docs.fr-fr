---
title: "Configurer le Pare-feu Windows pour le d&#233;bogage distant | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Configurer le Pare-feu Windows pour le d&#233;bogage distant
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment configurer le pare\-feu pour activer le débogage distant sur des ordinateurs qui exécutent les systèmes d’exploitation suivants :  
  
-   Windows 7  
  
-   Windows 8\/8.1  
  
-   Windows 10  
  
-   Windows Server 2008 \(R2\)  
  
-   Windows Server 2012  
  
-   Windows Server 2012 R2  
  
 Si le réseau sur lequel vous effectuez un débogage n’est pas protégé par un pare\-feu, cette configuration est inutile. Dans le cas contraire, il est nécessaire d’apporter des modifications à la configuration du pare\-feu pour l’ordinateur qui héberge Visual Studio et l’ordinateur distant qui doit être débogué.  
  
 **IPSec** Si votre réseau nécessite que la communication soit effectuée à l’aide d’IPSec, vous devez ouvrir des ports supplémentaires sur l’ordinateur hôte Visual Studio et l’ordinateur distant.  
  
 **Serveur web** Si vous déboguez un serveur web distant, vous devez ouvrir un port supplémentaire sur l’ordinateur distant.  
  
 Notez que les deux ordinateurs n’ont pas à exécuter le même système d’exploitation. Par exemple, l’ordinateur Visual Studio peut exécuter Windows 10 et l’ordinateur distant peut exécuter Windows Server 2012 R2.  
  
## Pour configurer le Pare\-feu Windows sur l’ordinateur Visual Studio  
 Les instructions pour configurer le Pare\-feu Windows diffèrent légèrement en fonction des systèmes d’exploitation. Sur Windows 7 ou Windows Server 2008, le mot **programme** est utilisé ; sur Windows 8\/8.1, Windows 10 et Windows Server 2012, le mot **application** est utilisé.  Dans les étapes suivantes, nous allons utiliser le mot **application**.  
  
1.  Ouvrez la page Pare\-feu Windows. \(Dans la zone de recherche du menu **Démarrer**, tapez **Pare\-feu Windows**.\)  
  
2.  Cliquez sur **Autoriser une application ou une fonctionnalité via le Pare\-feu Windows**.  
  
3.  Dans la liste **Applications et fonctionnalités autorisées**, recherchez **Détection du débogueur distant de Visual Studio**. Si l’option est répertoriée, assurez\-vous qu’elle est sélectionnée et qu’un ou que plusieurs types de réseau sont également sélectionnés.  
  
4.  Si l’option **Détection du débogueur distant de Visual Studio** n’est pas répertoriée, cliquez sur **Autoriser une autre application**. Si l’option n’est toujours pas visible dans la fenêtre **Ajouter une application**, cliquez sur **Parcourir** et accédez à **\<répertoire d’installation de Visual Studio\>\\Common7\\IDE\\Remote Debugger**. Recherchez le dossier approprié pour l’application \(x86, x64, Appx\), puis sélectionnez **msvsmon.exe**. Cliquez ensuite sur **Ajouter**.  
  
5.  Dans la liste **Applications et fonctionnalités autorisées**, sélectionnez **Visual Studio Remote Debugging Monitor**. Cochez un ou plusieurs types de réseau \(**Domaine, Domestique\/entreprise \(privé\), Public**\) avec lesquels vous souhaitez que Remote Debugging Monitor communique. Les types doivent inclure le réseau auquel l’ordinateur Visual Studio est connecté.  
  
## Pour ouvrir un port sur l’ordinateur Visual Studio pour activer la détection  
 Vous devez permettre au port UDP 3702 entrant d’autoriser la détection du ou des ordinateurs qui exécutent le débogueur distant. Pour l’ajouter, consultez Comment configurer des ports dans un pare\-feu.  
  
## Pour configurer le Pare\-feu Windows de l’ordinateur distant pour le débogage distant  
 Les composants de débogage distant peuvent être installés sur l’ordinateur distant ou exécutés à partir d’un répertoire partagé. Le pare\-feu de l’ordinateur distant doit être configuré dans les deux cas. Les composants de débogage distants sont situés dans :  
  
 **\<répertoire d’installation de Visual Studio\>\\Common7\\IDE\\Remote Debugger**  
  
 Les instructions pour configurer le Pare\-feu Windows diffèrent légèrement en fonction des systèmes d’exploitation. Sur Windows 7 ou Windows Server 2008, le mot **programme** est utilisé ; sur Windows 8\/8.1, Windows 10 et Windows Server 2012, le mot **application** est utilisé.  Dans les étapes suivantes, nous allons utiliser le mot **application**.  
  
1.  Ouvrez la page Pare\-feu Windows. \(Dans la zone de recherche du menu **Démarrer**, tapez **Pare\-feu Windows**.\)  
  
2.  Cliquez sur **Autoriser une application ou une fonctionnalité via le Pare\-feu Windows**.  
  
3.  Dans la liste **Applications et fonctionnalités autorisées**, recherchez **Visual Studio Remote Debugging Monitor**. Si l’option est répertoriée, assurez\-vous qu’elle est sélectionnée et qu’un ou que plusieurs types de réseau sont également sélectionnés.  
  
4.  Si l’option **Visual Studio Remote Debugging Monitor** n’est pas répertoriée, cliquez sur **Autoriser une autre application**. Si l’option n’est toujours pas visible dans la fenêtre **Ajouter une application**, cliquez sur **Parcourir** et accédez à **\<répertoire d’installation de Visual Studio\>\\Common7\\IDE\\Remote Debugger**. Recherchez le dossier approprié pour l’application \(x86, x64, Appx\), puis sélectionnez **msvsmon.exe**. Cliquez ensuite sur **Ajouter**.  
  
5.  Dans la liste **Applications autorisées**, sélectionnez **Visual Studio Remote Debugging Monitor**. Cochez un ou plusieurs types de réseau \(**Domaine, Domestique\/entreprise \(privé\), Public**\) avec lesquels vous souhaitez que Remote Debugging Monitor communique. Les types doivent inclure le réseau auquel l’ordinateur Visual Studio est connecté.  
  
## Ports sur l’ordinateur distant qui permettent le débogage distant  
  
|||||  
|-|-|-|-|  
|**Ports**|**Entrant\/sortant**|**Protocole**|**Description**|  
|3702|Sortant|UDP|Requis pour la détection du débogueur distant.|  
|4020||TCP|Pour VS 2015. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez Affectations de port du débogueur distant de Visual Studio.|  
|4021||TCP|Pour VS 2015. Le numéro de port est incrémenté de 2 pour chaque version de Visual Studio. Pour plus d’informations, consultez Affectations de port du débogueur distant de Visual Studio.|  
  
## Ports sur l’ordinateur distant qui permettent le débogage distant avec le mode de compatibilité managé ou natif  
  
|||||  
|-|-|-|-|  
|**Ports**|**Entrant\/sortant**|**Protocole**|**Description**|  
|135, 139, 445|Sortant|TCP|Requis.|  
|137, 138|Sortant|UDP|Requis.|  
|500, 4500|Sortant|UDP|Requis si votre stratégie de domaine nécessite que la communication réseau soit effectuée via IPSec.|  
|80|Sortant|TCP|Requis pour le débogage du serveur web.|  
  
## Comment configurer des ports dans le Pare\-feu Windows  
  
1.  Dans le menu **Démarrer**, recherchez **Pare\-feu Windows avec sécurité avancée**.  
  
2.  Cliquez sur **Règles de trafic entrant** ou **Règles de trafic sortant**, puis sur **Nouvelle règle** dans la liste **Actions**.  
  
3.  Dans la page **Type de règle**, sélectionnez **Port**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Protocole et ports**, sélectionnez le protocole de port \(TCP ou UDP\). Sélectionnez **Ports locaux spécifiques** et entrez un ou plusieurs numéros de port que vous souhaitez activer pour le protocole. Séparez les numéros par des virgules. Cliquez ensuite sur **Suivant**.  
  
5.  Dans la page **Action**, sélectionnez **Autoriser la connexion**, puis cliquez sur **Suivant**.  
  
6.  Dans la page **Profil**, sélectionnez un ou plusieurs types de réseau à activer pour le port. Les types que vous sélectionnez doivent inclure le réseau auquel l’ordinateur distant est connecté. Cliquez ensuite sur **Suivant**.  
  
7.  Dans la page **Nom**, tapez un nom pour la règle, puis cliquez sur **Terminer**.  
  
8.  Vous devez voir votre nouvelle règle dans la liste **Règles de trafic entrant** ou **Règles de trafic sortant**.  
  
## Voir aussi  
 [Débogage distant](../debugger/remote-debugging.md)