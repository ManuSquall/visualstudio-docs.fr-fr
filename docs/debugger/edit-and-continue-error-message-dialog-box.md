---
title: Modifier & Continuer, boîte de dialogue erreur Message | Documents Microsoft
ms.custom: ''
ms.date: 06/22/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b521eafcc62a49f2dd2a4c327158070bdbe62ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Message d'erreur de Modifier & Continuer, boîte de dialogue
Cette boîte de dialogue s’affiche lorsque vous déboguez dans un langage qui prend en charge Modifier & Continuer, mais **Modifier & Continuer** n’est pas disponible pour le type de modifications de code que vous avez apportées. Le message d'erreur affiché dans la boîte de dialogue fournit une explication plus détaillée. Les raisons pouvant justifier l'affichage de cette boîte de dialogue sont les suivantes :  

-   Vous avez essayé de modifier le code SQL Server.

-   Vous avez essayé de modifier un code optimisé. (Vous devrez peut-être passer d’une version Release à une version debug.)

-   Vous avez essayé de modifier le code pendant son exécution (au lieu de pendant la suspension dans le débogueur). Essayez [définissant un point d’arrêt](../debugger/using-breakpoints.md) et modification du code pendant la suspension.

-   Vous avez essayé de modifier un code managé alors que le débogage non managé était activé. Modifier & Continuer ne fonctionne pas avec [le débogage en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).

-   Vous modifié un code qui n’est pas pris en charge par Modifier & Continuer dans votre langage de programmation. Pour plus d’informations, consultez les rubriques pour les modifications du code non pris en charge dans [c#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), et [C++](../debugger/supported-code-changes-cpp.md).
  
-   Vous avez essayé de modifier le code dans un programme que vous avez joint à plutôt que de démarrer à partir de la **déboguer** menu.  
  
-   Vous avez essayé de modifier le code en déboguant un Dr. Dr. Watson.  
  
-   Vous avez essayé de modifier le code après une exception non gérée s’est produite et l’option «**dérouler la pile des appels sur les exceptions non gérées**» n’a été sélectionné.  
  
-   Vous avez essayé de modifier le code pendant le débogage d'une application d'exécution incorporée.
  
-   Vous avez essayé de modifier le code managé à l’aide de la version du .NET Framework avant 4.5.1 et la cible est une application 64 bits. Pour utiliser Modifier & Continuer, vous devez affecter x86 à la cible. (*nom_projet* **propriétés**, **compiler** onglet, **avancés du compilateur** paramètre.).  
  
-   Vous avez tenté de modifier le code d'un assembly qui a été modifié pendant le débogage et a été rechargé.  
  
-   Vous avez tenté de modifier le code d'un assembly qui n'a pas été chargé.  
  
-   Vous avez commencé à déboguer une version ancienne de votre application (étant donné que la nouvelle version comporte des erreurs de build).
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **OK**  
 Fermez la boîte de dialogue et annulez la tentative de modification précédente.  
  
## <a name="see-also"></a>Voir aussi  
 [C++ Modifier & Continuer blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Modifications de code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)