---
title: Utilisation de Windows Runtime dans JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571459"
---
# <a name="using-the-windows-runtime-in-javascript"></a>Utilisation de Windows Runtime dans JavaScript
Quand vous écrivez une application pour la plateforme Windows universelle (UWP), vous pouvez utiliser les classes, méthodes et propriétés Windows Runtime de façon similaire aux objets, méthodes et propriétés JavaScript natifs. Cette rubrique fournit des informations préliminaires et des liens vers des rubriques qui expliquent les concepts de base de l'utilisation des API Windows Runtime dans JavaScript, notamment la façon dont les types Windows Runtime sont représentés, la manière d'utiliser les méthodes Windows Runtime asynchrones et la façon d'écouter et gérer les événements Windows Runtime.  
  
 Pour obtenir la documentation de référence du langage JavaScript, consultez [Informations de référence sur le langage JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s’exécutent dans Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Documentation de référence sur Windows Runtime  
 Pour obtenir une documentation de référence, consultez [Informations de référence sur Windows Runtime](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Des exemples de code sont disponibles en JavaScript, ainsi qu'en C++, C# et Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Écriture de composants Windows Runtime en C++, C# ou Visual Basic  
 Pour obtenir des instructions et des recommandations sur l’écriture de composants Windows Runtime pouvant être utilisés dans JavaScript, consultez [Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) et [Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Conventions de casse avec les fonctionnalités Windows Runtime  
 Les conventions de casse pour les fonctionnalités Windows Runtime en JavaScript diffèrent légèrement de celles utilisées dans les autres langages :  
  
-   Les espaces de noms et les classes sont en casse Pascal :  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Les membres des classes, y compris les méthodes et les propriétés, ainsi que les membres des structures et énumérations, sont en casse mixte :  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Les noms d'événements sont en minuscules :  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur l’utilisation de l’API Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Utilisation de méthodes asynchrones Windows Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Gestion des événements Windows Runtime dans JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Représentation JavaScript des types Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Projection JavaScript des DateTime et TimeSpan de Windows Runtime](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)