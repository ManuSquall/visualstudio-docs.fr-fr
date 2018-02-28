---
title: EVALFLAGS90 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 80f281e65d4dd7b2df24233552bdc46d4b29bebe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="evalflags90"></a>EVALFLAGS90
Énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression. Cette énumération étend la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 EVAL90_RETURNVALUE  
 Spécifie que la valeur renvoyée, le cas échéant, être évaluées.  
  
 EVAL90_NOSIDEEFFECTS  
 Spécifie que les effets secondaires ne seront ne pas autorisées.  
  
 EVAL90_ALLOWBPS  
 Spécifie l’arrêt sur les points d’arrêt.  
  
 EVAL90_ALLOWERRORREPORT  
 Spécifie ce rapport d’erreurs à l’hôte pour être autorisée. Principalement utilisé pour l’évaluation d’expression dans le script dans Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Fonctions de force à évaluer en tant qu’adresses, au lieu d’appeler la fonction.  
  
 EVAL90_NOFUNCEVAL  
 Fonction empêche d’en cours d’évaluation. Par exemple, considérez la `int` jeton dans l’expression `myExpression(int) + 10`. Cette fonction peut être évaluée correctement en tant qu’adresse, mais pas en tant que valeur.  
  
 EVAL90_NOEVENTS  
 Indicateur pour indiquer que les événements qui se produisent pendant l’évaluation d’expression ne doivent pas être envoyées vers le Gestionnaire de session de débogage (SDM) ou à l’IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Permet d’évaluation d’expression au moment du design.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Permet la création de variables implicite.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Évaluation de force à se produire immédiatement. Cela est utile lorsque le traitement d’une demande, telle qu’une demande de l’utilisateur.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg90.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)