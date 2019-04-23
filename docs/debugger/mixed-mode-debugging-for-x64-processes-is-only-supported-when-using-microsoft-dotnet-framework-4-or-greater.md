---
title: En mode mixte débogage pour x64 processus est uniquement pris en charge lors de l’utilisation de Microsoft.NET Framework 4 ou supérieur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 821efec0beb26cea150fe0cfac20f0dc4c45d5f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057808"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
Les versions du .NET Framework antérieures à la version 4 ne prennent pas en charge le débogage en mode mixte des processus x64. Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.

### <a name="workarounds"></a>Solutions

- Mettez votre projet à jour de façon à utiliser Microsoft .NET Framework 4 ou version ultérieure.

     - ou -

     Déboguez votre code managé et natif dans des sessions de débogage distinctes.

     - ou -

     Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Pour passer en plateforme 32 bits (Visual Basic ou C#)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

2. Dans les pages de propriétés, cliquez sur l’onglet **Compiler** ou **Déboguer**.

3. Cliquez sur **Plateforme** et sélectionnez x86 dans la liste.

     Par défaut, les compilateurs C# et Visual Basic génèrent du code à exécuter sur n'importe quelle UC. Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits. Pour une exécution sur un processus 32 bits, vous devez sélectionner **Win32**, et non pas **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Pour passer en plateforme 32 bits (C/C++)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Propriétés**.

2. Dans les pages de propriétés, cliquez sur **Plateforme**, puis sélectionnez Win32 dans la liste.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Consultez [configuration du débogage SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)