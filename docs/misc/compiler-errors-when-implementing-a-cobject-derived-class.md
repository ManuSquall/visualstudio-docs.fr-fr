---
title: "Erreurs du compilateur lors de l’impl&#233;mentation d’une classe d&#233;riv&#233;e CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compilation du code source, classes dérivées CObject"
  - "erreurs (C++)"
  - "erreurs (C++), compilateur"
  - "classe CObject, erreurs du compilateur pour les classes dérivées"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Erreurs du compilateur lors de l’impl&#233;mentation d’une classe d&#233;riv&#233;e CObject
Si vous implémentez une classe dérivée de `CObject` et si votre code est écrit de sorte que le constructeur de copie ou l’opérateur d’assignation de la classe doit être appelé, le compilateur peut signaler des erreurs similaires à celles\-ci :  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Vous pouvez reproduire le problème en compilant l’exemple de la section Exemple de code ci\-dessous.  
  
> [!NOTE]
>  L’exemple de code présenté dans cet article génère les messages d’erreur suivants :  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Ces erreurs de compilation se produisent, car `CObject` déclare un constructeur de copie et un opérateur d’assignation privés dans le fichier AFX.h. Le compilateur ne génère donc pas de constructeur de copie ni d’opérateur d’assignation par défaut pour la classe dérivée de `CObject`. Étant donné que le compilateur ne trouve pas ces fonctions déclarées dans la classe, il signale ces erreurs.  
  
 Pour éviter les erreurs de compilation, vous devez implémenter un constructeur de copie et un opérateur d’assignation pour la classe dérivée de `CObject`. Cette procédure est expliquée dans l’exemple de code ci\-dessous. Vous pouvez éviter ces erreurs en supprimant les commentaires des lignes indiquées dans l’exemple de code.  
  
## Exemple de code  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## Voir aussi  
 [Avertissement du compilateurs C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)