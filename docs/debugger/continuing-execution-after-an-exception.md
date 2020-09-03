---
title: Poursuite de l’exécution après une exception | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e94867d845988b787247c32d32afd35af946972
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350678"
---
# <a name="continuing-execution-after-an-exception"></a>Poursuite de l'exécution à la suite d'une exception
Lorsque le débogueur interrompt l’exécution en raison d’une exception, vous verrez l' **assistance d’exception**, par défaut. Si vous avez désactivé le **programme d’assistance** de l’exception dans la boîte de dialogue **options** , l' **Assistant Exception** (C# ou Visual Basic) ou la boîte de dialogue d' **exception** (C++) s’affichent.

 Lorsque l' **assistance d’exception** s’affiche, vous pouvez essayer de résoudre le problème à l’origine de l’exception.

## <a name="managed-and-native-code"></a>Code managé et natif
 Dans du code managé et natif, vous pouvez continuer l’exécution dans le même thread après une exception non gérée. L' **assistance** de l’exception déroulera la pile des appels jusqu’au point où l’exception a été levée.

## <a name="mixed-code"></a>Code mixte
 Si une exception non gérée se produit durant le débogage d'un code mixte natif et managé, les contraintes du système d'exploitation empêchent le déroulement de la pile des appels. Si vous essayez de rembobiner la pile des appels via le menu contextuel, un message d'erreur explique que le débogueur ne peut pas dérouler à partir d'une exception non gérée lors du débogage de code mixte.

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)