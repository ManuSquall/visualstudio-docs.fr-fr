---
title: Modifier et continuer, boîte de dialogue erreur message | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47693c6fbb25fb0a7c2468abbad515f8aaf63159
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694983"
---
# <a name="edit-and-continue-error-message"></a>Modifier & Continuer le message d’erreur

Le **Modifier & Continuer** boîte de message d’erreur s’affiche lorsque vous déboguez dans un langage de code qui prend en charge Modifier & Continuer, mais Modifier & Continuer n’est pas disponible pour les modifications de code que vous avez apportées. Le message d’erreur fournit une explication plus détaillée. Pour répondre à la boîte de dialogue, sélectionnez **OK** pour fermer la boîte de dialogue et annulez la tentative de modification.

Les raisons possibles de ce message d’erreur sont les suivantes :

-   Essayez de modifier le code de SQL Server.
-   Essayez de modifier un code optimisé. Vous devrez peut-être passer d’une version Release à une version debug.
-   Essayez de modifier le code pendant son exécution, au lieu de pendant la suspension dans le débogueur. Essayez [définissant un point d’arrêt](../debugger/using-breakpoints.md)et modifier le code pendant la suspension.
-   Essayez de modifier du code managé lorsque seulement le débogage non managé est activé. Modifier & Continuer ne fonctionne pas avec [le débogage en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).
-   Changer d’un code qui n’est pas pris en charge par Modifier & Continuer dans votre langage de programmation. Pour plus d’informations, consultez les articles [pris en charge les modifications de code dans C# ](supported-code-changes-csharp.md), [non pris en charge des modifications dans Visual Basic Modifier & Continuer](/visualstudio/debugger/supported-code-changes-csharp), et [pris en charge les modifications du code C++](supported-code-changes-cpp.md).
-   Essayez de modifier le code dans une application que vous êtes attaché, au lieu de démarrer le débogage à partir de la **déboguer** menu.
-   Essayez de modifier le code en déboguant un Dr. Dr. Watson.
-   Essayez de modifier le code après une exception non gérée se produit et l’option **dérouler la pile des appels sur les exceptions non gérées** n’est pas sélectionnée.
-   Essayez de modifier du code pendant le débogage d’une application runtime incorporée.
-   Essayez de modifier du code managé à l’aide d’une version de .NET Framework antérieures à 4.5.1 avec une cible de l’application 64 bits. Pour utiliser Modifier & Continuer pour .NET Framework antérieures à 4.5.1, définissez la cible sur **x86** dans le  **\<nom_projet >** > **propriétés**  >  **Compiler** onglet, **paramètres avancés du compilateur** paramètre.
-   Essayez de modifier le code dans un assembly qui a été modifié pendant le débogage et a été rechargé.
-   Essayez de modifier le code dans un assembly qui n’a pas été chargé.
-   Commencer à déboguer une ancienne version d’une application, car la version la plus récente a des erreurs de build.

Pour plus d'informations, voir :
- [C++ modifier et continuer blog publier](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Modifications de code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)
- [Modifier & Continuer](../debugger/edit-and-continue.md)