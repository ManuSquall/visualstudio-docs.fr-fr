---
title: Boîte de dialogue Modifier & Continuer-message d’erreur | Microsoft Docs
description: Modifier & continuer peut signaler qu’il n’est pas disponible pour vos modifications de code. Cet article présente les raisons possibles.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0835746b94412380bee314bc3fac59b4c48f86d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871999"
---
# <a name="edit-and-continue-error-message"></a>Message d’erreur modifier & continuer

La boîte de message d’erreur **modifier & continuer** s’affiche lorsque vous effectuez un débogage dans un langage de code qui prend en charge modifier & continuer, mais que modifier & Continuer n’est pas disponible pour les modifications de code que vous avez apportées. Le message d’erreur fournit une explication plus détaillée. Pour répondre à la boîte de dialogue, sélectionnez **OK** pour fermer la boîte de dialogue et annuler la tentative de modification.

Les raisons possibles de ce message d’erreur sont les suivantes :

- Tentative de modification du code d’SQL Server.
- Tentative de modification du code optimisé. Vous devrez peut-être basculer d’une version release vers une version Debug.
- Tentative de modification du code pendant son exécution, au lieu de l’être en pause dans le débogueur. Essayez [de définir un point d’arrêt](../debugger/using-breakpoints.md)et de modifier le code en pause.
- Tentative de modification du code managé lorsque seul le débogage non managé est activé. Modifier & Continuer ne fonctionne pas avec [le débogage en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).
- Apporter une modification de code qui n’est pas prise en charge par modifier & continuer dans votre langage de programmation. Pour plus d’informations, consultez les articles sur [les modifications de code prises en charge en C#](supported-code-changes-csharp.md), les modifications [non prises en charge dans Visual Basic modifier & Continuer](supported-code-changes-csharp.md)et [les modifications de code C++ prises en charge](supported-code-changes-cpp.md).
- Tentative de modification du code dans une application à laquelle vous êtes attaché, au lieu de démarrer le débogage à partir du menu **Déboguer** .
- Tentative de modification du code lors du débogage d’un vidage Dr. Watson.
- La tentative de modification du code après une exception non gérée se produit, et l’option **dérouler la pile des appels sur les exceptions non gérées** n’est pas sélectionnée.
- Tentative de modification du code lors du débogage d’une application Runtime incorporée.
- Tentative de modification du code managé à l’aide d’une version .NET Framework antérieure à 4.5.1 avec une cible d’application 64 bits. Pour utiliser modifier & Continuer pour .NET Framework antérieur à la version 4.5.1, définissez la cible sur **x86** dans l’onglet Propriétés de la **\<ProjectName>**  >    >  **compilation** , paramètres **avancés du compilateur** .
- Tentative de modification du code dans un assembly qui a été modifié pendant le débogage et qui a été rechargé.
- Tentative de modification du code dans un assembly qui n’a pas été chargé.
- Démarrage du débogage d’une ancienne version d’une application, car la version la plus récente contient des erreurs de Build.

Pour plus d'informations, consultez les pages suivantes :
- [Billet de blog modifier & Continuer pour C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Modifications du code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)
- [Modifier &amp; Continuer](../debugger/edit-and-continue.md)