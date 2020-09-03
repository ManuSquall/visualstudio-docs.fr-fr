---
title: Le débogage en mode mixte est pris en charge uniquement lors de l’utilisation de Microsoft .NET Framework 2,0 ou 3,0 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b20ef6b81e4d7162fd230d9d0c3437fe1b5232c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72730914"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Le débogage en mode mixte est uniquement pris en charge lorsque vous utilisez Microsoft .NET Framework 2.0 ou 3.0
Les versions de Microsoft .NET Framework antérieures à la version 2.0 ne prennent pas en charge le débogage en mode mixte de processus 64 bits. Cela signifie que vous ne pouvez pas passer du code managé au code natif, ou inversement, lorsque vous procédez au débogage.

 Pour éviter ce problème, vous pouvez :

- mettre à jour votre projet pour utiliser Microsoft .NET Framework 2.0 ou 3.0 ;

- Déboguez votre code managé et natif dans des sessions de débogage distinctes.

- Déboguez votre code mixte en tant que processus 32 bits, de la façon décrite dans les procédures suivantes.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Pour faire passer le système d'exploitation à 32 bits (Visual Basic ou C#)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.

2. Dans les pages de propriétés, cliquez sur l’onglet **Compiler** ou **Déboguer**.

3. Cliquez sur **Plateforme**, puis sélectionnez **x86** dans la liste de plateformes.

     Par défaut, les compilateurs C# et Visual Basic génèrent le code à exécuter sur n'importe quelle UC. Sur un ordinateur 64 bits, ces fichiers binaires sont exécutés en tant que processus 64 bits. Pour une exécution sur un processus 32 bits, vous devez sélectionner **Win32**, et non pas **AnyCPU**.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Pour faire passer le système d'exploitation à 32 bits (C/C++)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés** dans le menu contextuel.

     Dans les pages de propriétés, cliquez sur **Plateforme**, puis sélectionnez **Win32** dans la liste de plateformes.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Consultez [configuration du débogage SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)