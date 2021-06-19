---
title: Examiner le code système après une exception | Microsoft Docs
description: Découvrez comment examiner du code dans un appel système pour déterminer la cause de l’exception. La procédure s’applique même si les symboles du code système n’ont pas été chargés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f05ae1486089eaa63ef47a9953578db2a0b6662a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384653"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Comment : examiner du code système après une exception
Lorsqu'une exception est levée, il peut s'avérer nécessaire d'examiner le code dans un appel système afin de déterminer la cause de l'exception. Pour ce faire, suivez la procédure ci-dessous si aucun symbole n'est chargé pour le code système ou si l'option Uniquement mon code est activée.

### <a name="to-examine-system-code-following-an-exception"></a>Pour examiner du code système après une exception

1. Cliquez avec le bouton droit dans la fenêtre **Pile des appels**, puis cliquez sur **Afficher le code externe**.

     Si l'option Uniquement mon code n'est pas activée, cette option n'est pas disponible dans le menu contextuel et le code système s'affiche par défaut.

2. Cliquez avec le bouton droit sur les frames de code externe qui s’affichent à présent dans la fenêtre **Pile des appels**.

3. Pointez sur **Charger les symboles depuis** et cliquez sur **Serveurs de symboles Microsoft**.

    1. Si l'option Uniquement mon code était activée, une boîte de dialogue s'affiche pour indiquer que cette option est à présent désactivée, ce qui est nécessaire pour effectuer un pas à pas détaillé dans les appels système.

    2. La boîte de dialogue **Téléchargement des symboles publics** apparaît. puis se ferme une fois le téléchargement terminé.

4. Vous pouvez à présent examiner le code système dans la fenêtre **Pile des appels** et dans d’autres fenêtres. Par exemple, vous pouvez double-cliquer sur une frame de pile d’appels pour afficher le code dans une fenêtre **Code Machine** ou source.

## <a name="see-also"></a>Voir aussi
- [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)