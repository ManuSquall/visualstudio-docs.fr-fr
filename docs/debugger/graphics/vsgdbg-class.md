---
title: Vsgdbg, classe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f457d35725a0a6041fe82b06853a6dffdf69b53d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922453"
---
# <a name="vsgdbg-class"></a>VsgDbg, classe
Représente une interface pour un contrôle par programmation du composant dans l’application de graphics diagnostics.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Membres  
 Le `VsgDbg` classe prend en charge les membres suivants.  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Name|Description|  
|----------|-----------------|  
|[VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)|Construit une instance de la `VsgDbg` classe et prépare éventuellement le composant dans l’application de graphics diagnostics activement capturer et enregistrer des informations graphiques.|  
|[VsgDbg::~VsgDbg, destructeur](vsgdbg-tilde-vsgdbg-destructor.md)|Détruit une instance de la `VsgDbg` classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Ajoute un message personnalisé pour les diagnostics graphiques HUD (Head-Up Display).|  
|[BeginCapture](begincapture.md)|Commence un intervalle de capture s’achèvera par `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Capture le reste de l’image actuelle dans le fichier journal de graphiques.|  
|[Copier (capture par programmation)](copy-programmatic-capture.md)|Copie le contenu du fichier journal (.vsglog) tracé actif dans un nouveau fichier.|  
|[EndCapture](endcapture.md)|Met fin à un intervalle de capture a été démarré avec `BeginCapture`.|  
|[Init](init.md)|Prépare le composant dans l’application de graphics diagnostics activement capturer et enregistrer des informations graphiques.|  
|[ToggleHUD](togglehud.md)|Active ou désactive le segment de recouvrement graphics diagnostics HUD activé ou désactivé.|  
|[UnInit](uninit.md)|Finalise le fichier journal de graphisme, il ferme et libère les ressources qui ont été utilisés pendant que l’application a été enregistre activement les informations graphiques.|  
  
## <a name="remarks"></a>Notes  
 Le `VsgDbg` classe représente une interface qui vous permettent de contrôler par programme les fonctionnalités graphics diagnostics. Vous pouvez utiliser certaines fonctionnalités même lorsque vous n’êtes pas activement capturer et enregistrer les informations graphiques ; Cela inclut la `AddMessage` fonction membre et `ToggleHUD` fonction membre. Les autres fonctions membres de préparer le composant dans l’application de graphics diagnostics pour démarrer ou arrêter la capture des informations graphiques actifs ou doivent être appelées pendant que l’application est activement capturer et enregistrer des informations graphiques dans un fichier journal de graphisme.