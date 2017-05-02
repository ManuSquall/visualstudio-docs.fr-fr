---
title: "Utilisation de Windows Runtime dans JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows Runtime."
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilisation de Windows Runtime dans JavaScript
Quand vous écrivez une application du [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] ou du Windows Phone Store en JavaScript, vous pouvez utiliser les classes, les méthodes et les propriétés Windows Runtime de façon similaire aux objets, méthodes et propriétés JavaScript natifs.  Cette rubrique fournit des informations préliminaires et des liens vers des rubriques qui expliquent les concepts de base de l'utilisation des API Windows Runtime dans JavaScript, notamment la façon dont les types Windows Runtime sont représentés, la manière d'utiliser les méthodes Windows Runtime asynchrones et la façon d'écouter et gérer les événements Windows Runtime.  
  
 Pour consulter la documentation de référence JavaScript, reportez\-vous à la [Informations de référence sur le langage JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s'exécutent dans Internet Explorer.  
  
## Documentation de référence sur Windows Runtime  
 Pour consulter la documentation de référence, voir [Windows Runtime reference](http://msdn.microsoft.com/fr-fr/8fe97dbf-8cd4-435f-b481-9e83d0519f9e).  Des exemples de code sont disponibles en JavaScript, ainsi qu'en C\+\+, C\# et Visual Basic.  
  
## Écriture de composants Windows Runtime en C\+\+, C\# ou Visual Basic  
 Pour obtenir des instructions et des consignes pour écrire des composants Windows Runtime qui peuvent être consommés en JavaScript, consultez [Création de composants Windows Runtime](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133).  
  
## Conventions de casse avec les fonctionnalités Windows Runtime  
 Les conventions de casse pour les fonctionnalités Windows Runtime en JavaScript diffèrent légèrement de celles utilisées dans les autres langages :  
  
-   Les espaces de noms et les classes sont en casse Pascal :  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Les membres des classes, y compris les méthodes et les propriétés, ainsi que les membres des structures et énumérations, sont en casse mixte :  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Les noms d'événements sont en minuscules :  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## Voir aussi  
 [Considérations relatives à l'utilisation de l'API Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Utilisation des méthodes Windows Runtime asynchrones](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Gestion des événements Windows Runtime dans JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Représentation JavaScript des types Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Projection JavaScript des DateTime et TimeSpan de Windows Runtime](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)