---
title: "Débogage d’un contrôle ActiveX de liés aux données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 32cbb7bee21b54c932e0c369c46c3b2c3dacd898
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-a-data-bound-activex-control"></a>Débogage d'un contrôle ActiveX lié aux données
Si vous développez un contrôle ActiveX qui sera lié à un contrôle de source de données, vous pouvez créer votre propre application conteneur et utiliser ce conteneur pour le débogage du contrôle ActiveX.  
  
 Par exemple, vous pouvez créer une application MFC basée sur des boîtes de dialogue et placer votre contrôle lié aux données et un contrôle de source de données dans la boîte de dialogue. Vous pouvez utiliser cette application MFC pour le test d'exécution et comme exécutable conteneur pour déboguer votre contrôle ActiveX lié aux données.  
  
## <a name="using-the-test-container"></a>Utilisation de Test Container  
 Si vous voulez qu'un conteneur facilement modifiable prenne en charge plusieurs interfaces sur le contrôle ou le conteneur, utilisez ActiveX Test Container comme exécutable pour la session de débogage. Dans ActiveX Test Container, cliquez sur **Options** à partir de la **conteneur** menu pour activer plusieurs interfaces. Pour plus d’informations, consultez [test des propriétés et des événements avec le conteneur de Test](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Si vous avez besoin d'effectuer un pas à pas détaillé dans le code du conteneur pendant le débogage, utilisez la version Debug de votre conteneur ou utilisez la version Debug d'ActiveX Test Container. Pour plus d’informations, consultez [exemple TSTCON : ActiveX Control Test Container](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Contrôles ActiveX](/cpp/mfc/activex-controls)