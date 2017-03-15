---
title: "VsgDbg, classe | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg, classe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Représente une interface pour le contrôle par programmation du composant dans les applications du diagnostic graphiques.  
  
## Syntaxe  
  
```cpp  
class VsgDbg;  
```  
  
## Membres  
 La classe `VsgDbg` prend en charge les membres suivants :  
  
### Constructeurs publics  
  
|Nom|Description|  
|---------|-----------------|  
|[VsgDbg::VsgDbg, constructeur](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)|Construit une instance de la classe `VsgDbg` et prépare éventuellement le composant dans les applications du diagnostic graphiques à la capture et à l'enregistrement d'informations graphiques.|  
|[VsgDbg::~VsgDbg, destructeur](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Détruit une instance de la classe `VsgDbg`.|  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Ajoute un message personnalisé au diagnostic HUD \(affichage prend en tête élevée\) graphiques.|  
|[BeginCapture](../debugger/begincapture.md)|Démarre un intervalle de capture qui se termine avec `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Capture le reste du frame actuel dans le fichier journal de graphiques.|  
|[Copier \(capture par programmation\)](../debugger/copy-programmatic-capture.md)|Copie le contenu du fichier actif du journal de graphiques \(.vsglog\) dans un nouveau fichier.|  
|[EndCapture](../debugger/endcapture.md)|Termine un intervalle de capture qui a été démarré par `BeginCapture`.|  
|[Init](../debugger/init.md)|Prépare le composant dans les applications du diagnostic graphiques à capturer et enregistrer des informations graphiques.|  
|[ToggleHUD](../debugger/togglehud.md)|Bascule le on\/off recouvert par HUD de diagnostic graphiques.|  
|[UnInit](../debugger/uninit.md)|Finalise le fichier journal de graphiques, le ferme, et libère les ressources utilisées lorsque l'application enregistrait les informations graphiques.|  
  
## Remarques  
 La classe `VsgDbg` représente une interface que vous pouvez utiliser pour contrôler les fonctionnalités de diagnostique de graphiques par programme.  Vous pouvez utiliser certaines fonctionnalités même si vous ne capturez pas et n'enregistrez pas les informations graphiques ; cela inclut la fonction membre `AddMessage` et la fonction membre `ToggleHUD`.  Les autres fonctions membres suivantes préparent le composant dans les applications du diagnostic graphiques pour démarrer ou arrêter la capture active des informations graphiques, ou doivent être appelées lorsque l'application est active capturante et enregistrante les informations graphiques dans un fichier journal graphiques.