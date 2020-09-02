---
title: Vsgdbg,, classe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145692"
---
# <a name="vsgdbg-class"></a>VsgDbg, classe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Représente une interface pour le contrôle par programmation du composant dans l’application de Graphics Diagnostics.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Membres  
 La `VsgDbg` classe prend en charge les membres suivants.  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[VsgDbg::VsgDbg, constructeur](../debugger/vsgdbg-vsgdbg-constructor.md)|Construit une instance de la `VsgDbg` classe et prépare éventuellement le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques.|  
|[VsgDbg::~VsgDbg, destructeur](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Détruit une instance de la `VsgDbg` classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Ajoute un message personnalisé à l’affichage à haute vue de Graphics Diagnostics (affichage principal).|  
|[BeginCapture](../debugger/begincapture.md)|Commence un intervalle de capture qui se termine par `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Capture le reste du frame actuel dans le fichier journal de graphisme.|  
|[Copier (capture par programmation)](../debugger/copy-programmatic-capture.md)|Copie le contenu du fichier journal de graphisme actif (. vsglog) dans un nouveau fichier.|  
|[EndCapture](../debugger/endcapture.md)|Termine un intervalle de capture qui a été démarré avec `BeginCapture` .|  
|[Init](../debugger/init.md)|Prépare le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques.|  
|[ToggleHUD](../debugger/togglehud.md)|Active ou désactive la superposition HUD Graphics Diagnostics.|  
|[UnInit](../debugger/uninit.md)|Finalise le fichier journal de graphisme, le ferme et libère les ressources qui ont été utilisées pendant que l’application enregistrait activement des informations graphiques.|  
  
## <a name="remarks"></a>Notes  
 La `VsgDbg` classe représente une interface que vous pouvez utiliser pour contrôler les fonctionnalités des diagnostics de graphiques par programmation. Vous pouvez utiliser certaines fonctionnalités même si vous ne parvenez pas à capturer et à enregistrer activement des informations graphiques. Cela comprend la `AddMessage` fonction membre et la `ToggleHUD` fonction membre. Les autres fonctions membres préparent le composant dans l’application de Graphics Diagnostics pour démarrer ou arrêter la capture active des informations graphiques, ou doivent être appelées pendant que l’application capture et enregistre activement des informations graphiques dans un fichier journal de graphisme.
