---
title: EVALFLAGS90 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b52db3e6612e733649f4fb5d88b1e26c027f5fed
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256163"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Énumère les valeurs valides pour les indicateurs qui contrôlent l’évaluation de l’expression. Cette énumération étend la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Spécifie que la valeur renvoyée, le cas échéant, être évalué.  
  
 EVAL90_NOSIDEEFFECTS  
 Spécifie que les effets secondaires ne seront ne pas autorisées.  
  
 EVAL90_ALLOWBPS  
 Spécifie l’arrêt sur des points d’arrêt.  
  
 EVAL90_ALLOWERRORREPORT  
 Spécifie ce rapport d’erreurs à l’hôte pour être autorisée. Principalement utilisé pour l’évaluation de l’expression dans le script dans Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Fonctions de force à évaluer en tant qu’adresses, au lieu d’appeler la fonction.  
  
 EVAL90_NOFUNCEVAL  
 Fonction empêche d’en cours d’évaluation. Par exemple, considérez le `int` jeton dans l’expression `myExpression(int) + 10`. Cette fonction peut être correctement évaluée en tant qu’adresse, mais pas en tant que valeur.  
  
 EVAL90_NOEVENTS  
 Indicateur pour indiquer que les événements qui se produisent pendant l’évaluation d’expression ne doivent pas être envoyées pour le Gestionnaire de session de débogage (SDM) ou à l’IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Permet l’évaluation d’expression au moment du design.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Permet la création implicite de variables.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Évaluation de force à se produire immédiatement. Cela est utile lors de la maintenance d’une requête, telle qu’une demande utilisateur.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg90.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

