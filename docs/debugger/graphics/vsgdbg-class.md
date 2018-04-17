---
title: Vsgdbg, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a37c2313b35091b5f939526f58b73effde285fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="vsgdbg-class"></a>VsgDbg, classe
Représente une interface pour un contrôle par programmation du composant dans l’application de graphics diagnostics.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Membres  
 La `VsgDbg` classe prend en charge les membres suivants.  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)|Construit une instance de la `VsgDbg` classe et prépare éventuellement le composant dans l’application de graphics diagnostics pour activement capturer et enregistrer des informations graphiques.|  
|[VsgDbg::~VsgDbg, destructeur](vsgdbg-tilde-vsgdbg-destructor.md)|Détruit une instance de la `VsgDbg` classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Ajoute un message personnalisé pour les diagnostics graphiques HUD (Head-Up Display).|  
|[BeginCapture](begincapture.md)|Commence un intervalle de capture qui se termine par `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Capture le reste de l’image actuelle dans le fichier journal de graphiques.|  
|[Copier (capture par programmation)](copy-programmatic-capture.md)|Copie le contenu du fichier journal (.vsglog) graphique actif dans un nouveau fichier.|  
|[EndCapture](endcapture.md)|Met fin à un intervalle de capture qui a été démarré avec `BeginCapture`.|  
|[Init](init.md)|Prépare le composant dans l’application de graphics diagnostics pour activement capturer et enregistrer des informations graphiques.|  
|[ToggleHUD](togglehud.md)|Active ou désactive le segment de recouvrement graphics diagnostics HUD ou désactiver.|  
|[UnInit](uninit.md)|Finalise le fichier journal de graphisme, ferme et libère les ressources qui ont été utilisés lors de l’application a été enregistre activement les informations graphiques.|  
  
## <a name="remarks"></a>Notes  
 La `VsgDbg` classe représente une interface qui vous permet de contrôler par programme les fonctionnalités de graphics diagnostics. Vous pouvez utiliser certaines fonctionnalités même lorsque vous n’êtes pas activement capturer et enregistrer les informations graphiques ; Cela inclut la `AddMessage` fonction membre et `ToggleHUD` fonction membre. Les autres fonctions membres de préparer le composant dans l’application de graphics diagnostics pour démarrer ou arrêter la capture active d’informations graphiques ou doivent être appelées pendant que l’application est activement capturer et enregistrer les informations graphiques dans un fichier journal de graphisme.