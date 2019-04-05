---
title: Les affectations de Port du débogueur distant | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1e70ec3ba50e5be1ed532bb4a88cbdd500af09c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949188"
---
# <a name="remote-debugger-port-assignments"></a>Affectations de port du débogueur distant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur distant de Visual Studio peut s’exécuter comme une application ou un service en arrière-plan. Quand il est exécuté comme une application, il utilise un port qui est affecté par défaut comme suit :  
  
- Visual Studio 2015 : 4020  
  
- Visual Studio 2013 : 4018  
  
- Visual Studio 2012 : 4016  
  
  En d’autres termes, le numéro de port attribué au débogueur distant est incrémenté de 2 pour chaque version. Vous pouvez définir un numéro de port différent si vous le souhaitez. Nous expliquerons comment définir des numéros de port dans une section ultérieure.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port du débogueur distant sur les systèmes d’exploitation 32 bits  
 Le port TCP 4020 (dans Visual Studio 2015) est le port principal, qui est requis pour tous les scénarios. Vous pouvez le configurer à partir de la ligne de commande ou de la fenêtre du débogueur distant.  
  
 Dans la fenêtre du débogueur distant, cliquez sur **Outils/Options**, puis définissez le numéro de port TCP/IP.  
  
 Sur la ligne de commande, démarrez le débogueur distant avec le commutateur **/port** : **msvsmon /port \<numéro de port>**.  
  
 Tous les commutateurs de ligne de commande du débogueur distant sont disponibles dans l’aide du débogage distant (appuyez sur **F1** ou cliquez sur **Aide/Utilisation** dans la fenêtre du débogueur distant).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port du débogueur distant sur les systèmes d’exploitation 64 bits  
 Quand la version 64 bits du débogueur distant démarre, elle utilise le port 4020 par défaut.  Si vous déboguez un processus 32 bits, la version 64 bits du débogueur distant démarre une version 32 bits du débogueur distant sur le port 4021. Si vous exécutez le débogueur distant 32 bits, il utilise le port 4020 et 4021 n’est pas utilisé.  
  
 Ce port est configurable à partir de la ligne de commande : **Msvsmon /wow64port \<le numéro de port >**.  
  
## <a name="the-discovery-port"></a>Port de détection  
 UDP 3702 est utilisé pour rechercher des instances en cours d’exécution du débogueur distant sur le réseau (par exemple, la boîte de dialogue **Rechercher** dans la boîte de dialogue **Attacher au processus** ). Il est utilisé uniquement pour la découverte d’un ordinateur exécutant le débogueur distant ; il est facultatif si vous disposez d’une autre façon de connaître le nom ou l’adresse IP de l’ordinateur cible. Comme il s’agit d’un port standard pour la détection, le numéro de port ne peut pas être configuré.  
  
 Si vous ne souhaitez pas activer la découverte, vous pouvez démarrer msvsmon à partir de la ligne de commande avec la détection désactivée :  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Port du débogueur distant sur Azure  
 Les ports suivants sont utilisés par le débogueur distant sur Azure. Les ports sur le service cloud sont mappés aux ports sur la machine virtuelle individuelle. Tous les ports sont TCP.  
  
||||  
|-|-|-|  
|**Connexion**|**Port sur le service cloud**|**Port sur la machine virtuelle**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Voir aussi  
 [Remote Debugging](../debugger/remote-debugging.md)
