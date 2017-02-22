---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90 (énumération)"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

énumère les valeurs valides pour les balises qui évaluation de l'expression de contrôle.  cette énumération étend l'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .  
  
## Syntaxe  
  
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
  
```c#  
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
  
#### Paramètres  
 EVAL90\_RETURNVALUE  
 Spécifie que la valeur de retour, le cas échéant, est évaluée.  
  
 EVAL90\_NOSIDEEFFECTS  
 Spécifie que les effets secondaires pour ne pas être autorisé.  
  
 EVAL90\_ALLOWBPS  
 Spécifie arrêter sur les points d'arrêt.  
  
 EVAL90\_ALLOWERRORREPORT  
 Spécifie que rapport d'erreurs à l'hôte pour activer.  Utilisée pour l'évaluation d'une expression dans le script dans Internet Explorer.  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 Les forces fonctionne pour être évaluées comme adresses, au lieu d'appeler la fonction.  
  
 EVAL90\_NOFUNCEVAL  
 Empêché la fonction d'être évalué.  par exemple, considérez le jeton d' `int` dans l'expression `myExpression(int) + 10`.  cette fonction peut être correctement évaluée comme adresse, mais pas comme valeur.  
  
 EVAL90\_NOEVENTS  
 Indicateur pour signaler que des événements qui se produisent pendant l'évaluation d'une expression ne doivent pas être transmis au gestionnaire de débogage de \(SDM\) session ou à l'IDE.  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 Active l'évaluation d'une expression au moment de le design.  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 Permet la création de variable implicite.  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 Force l'évaluation pour l'exécution immédiate.  Cela est utile en entretenant une application \(par exemple, une demande de l'utilisateur.  
  
## Configuration requise  
 en\-tête : Msdbg90.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)