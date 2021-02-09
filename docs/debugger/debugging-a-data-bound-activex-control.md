---
title: Débogage d’un contrôle ActiveX Data-Bound | Microsoft Docs
description: Découvrez comment déboguer un contrôle ActiveX lié à un contrôle de source de données en créant une application de conteneur pour le débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24de30887185ce4520817904ec6348ef6276b6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872896"
---
# <a name="debugging-a-data-bound-activex-control"></a>Débogage d'un contrôle ActiveX lié aux données
Si vous développez un contrôle ActiveX qui sera lié à un contrôle de source de données, vous pouvez créer votre propre application conteneur et utiliser ce conteneur pour le débogage du contrôle ActiveX.

 Par exemple, vous pouvez créer une application MFC basée sur des boîtes de dialogue et placer votre contrôle lié aux données et un contrôle de source de données dans la boîte de dialogue. Vous pouvez utiliser cette application MFC pour le test d'exécution et comme exécutable conteneur pour déboguer votre contrôle ActiveX lié aux données.

## <a name="using-the-test-container"></a>Utilisation de Test Container
 Si vous voulez qu'un conteneur facilement modifiable prenne en charge plusieurs interfaces sur le contrôle ou le conteneur, utilisez ActiveX Test Container comme exécutable pour la session de débogage. Dans ActiveX Test Container, cliquez sur **Options** dans le menu **Conteneur** pour activer différentes interfaces. Pour plus d’informations, consultez [test des propriétés et des événements avec le conteneur de test](/cpp/mfc/testing-properties-and-events-with-test-container).

 Si vous avez besoin d'effectuer un pas à pas détaillé dans le code du conteneur pendant le débogage, utilisez la version Debug de votre conteneur ou utilisez la version Debug d'ActiveX Test Container. Pour plus d’informations, consultez [exemple TSTCON : ActiveX Control Test Container](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Voir aussi
- [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)
- [Contrôles ActiveX](/cpp/mfc/activex-controls)