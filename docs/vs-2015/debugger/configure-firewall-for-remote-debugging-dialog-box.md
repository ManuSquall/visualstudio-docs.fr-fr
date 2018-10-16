---
title: Configurer le pare-feu pour la boîte de dialogue de débogage à distance | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d273d1158d2a0d3c867605bc4f43a40be8e38314
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188550"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Configurer le pare-feu pour le débogage distant (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue apparaît lorsque le Pare-feu Windows empêche le débogueur de recevoir des informations via le réseau. Pour poursuivre le débogage distant, vous devez ouvrir une faille dans le pare-feu pour que le débogueur puisse recevoir des informations.  
  
> [!CAUTION]
>  L'ouverture d'une faille dans le pare-feu peut exposer votre ordinateur à des menaces de sécurité que le pare-feu est censé bloquer. L’ouverture d’une faille pour le débogage à distance débloque les ports 4020 et 4021 dans Visual Studio 2015. Dans d’autres versions de Visual Studio, des numéros de port différents sont utilisés. Pour plus d’informations, consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). De plus, il permet au débogueur d'ouvrir des ports supplémentaires. Pour plus d’informations, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Annuler le débogage distant**  
 Annule la tentative de débogage distant. Les paramètres de sécurité de votre ordinateur restent intacts.  
  
 **Débloquer le débogage distant à partir d’ordinateurs sur le réseau local (sous-réseau)**  
 Active le débogage distant d'ordinateurs sur votre sous-réseau local. Cela peut rendre vulnérables les ordinateurs sur votre sous-réseau local, mais le pare-feu continue à bloquer des informations provenant de l'extérieur du sous-réseau.  
  
 **Débloquer le débogage distant à partir de n’importe quel ordinateur**  
 Active le débogage distant d'ordinateurs n'importe où sur le réseau. Ce paramètre est le moins sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Configurer les outils à distance sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Informations de référence sur le débogage de l’interface utilisateur](../debugger/debugging-user-interface-reference.md)



