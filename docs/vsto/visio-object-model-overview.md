---
title: "Vue d&#39;ensemble du mod&#232;le objet Visio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visio (développement Office dans Visual Studio), modèle objet"
  - "modèles objet (développement Office dans Visual Studio), Office"
  - "modèles objet (développement Office dans Visual Studio), Visio"
  - "objets (développement Office dans Visual Studio), modèles objet Office"
  - "modèles objet Office"
  - "Visio (modèle objet)"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Vue d&#39;ensemble du mod&#232;le objet Visio
  Pour développer les solutions Office pour Microsoft Office Visio, vous pouvez interagir avec le modèle objet Visio. Ce modèle objet se compose de classes et d'interfaces qui sont fournies dans l'assembly PIA de Visio et définies dans l'espace de noms Microsoft.Office.Interop.Visio.  
  
 Cette rubrique propose une brève vue d'ensemble du modèle objet Excel. Pour plus d'informations sur l'utilisation du modèle objet Visio pour exécuter des tâches dans les projets Office, consultez les rubriques suivantes :  
  
-   [Utilisation de documents Visio](../vsto/working-with-visio-documents.md)  
  
-   [Utilisation de formes Visio](../vsto/working-with-visio-shapes.md)  
  
## Présentation du modèle objet Visio  
 Visio fournit de nombreux objets avec lesquels vous pouvez interagir. Ces objets sont organisés selon une hiérarchie qui suit étroitement l'interface utilisateur. En haut de la hiérarchie se trouve l'objet [Microsoft.Office.Interop.Visio.Application](HV10077088). Cet objet représente l'instance en cours de Visio. L'objet Microsoft.Office.Interop.Visio.Application contient les objets Microsoft.Office.Interop.Visio.Document et Microsoft.Office.Interop.Visio.Page , ainsi que les collections Microsoft.Office.Interop.Visio.Documents et Microsoft.Office.Interop.Visio.Pages. Chacun de ces objets et collections possède de nombreuses méthodes et propriétés auxquelles vous pouvez accéder pour le manipuler et interagir avec lui.  
  
 Pour plus d'informations, consultez la documentation de référence VBA pour les objets [Microsoft.Office.Interop.Visio.Application](HV10077088)[Microsoft.Office.Interop.Visio.Document](HV10077095) et [Microsoft.Office.Interop.Visio.Page](HV10077063), ainsi que pour les collections [Microsoft.Office.Interop.Visio.Documents](HV10077062) et [Microsoft.Office.Interop.Visio.Pages](HV10077074).  
  
 Les sections suivantes décrivent brièvement les objets de niveau supérieur et comment ils interagissent entre eux. Ces objets incluent les éléments suivants :  
  
-   Objet Application  
  
-   Objet Document  
  
-   Page \(objet\)  
  
### Objet Application  
 L'objet Microsoft.Office.Interop.Visio.Application représente l'application Visio et est le parent de tous les autres objets. Ses membres s'appliquent généralement à Visio dans son ensemble. Vous pouvez utiliser les propriétés et les méthodes des objets Microsoft.Office.Interop.Visio.Application et Microsoft.Office.Interop.Visio.ApplicationSettings pour contrôler l'environnement Visio.  
  
 Dans les projets de compléments VSTO, vous pouvez accéder à l'objet Microsoft.Office.Interop.Visio.Application à l'aide du champ `Application` de la classe `ThisAddIn`. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
### Objet Document  
 L'objet Microsoft.Office.Interop.Visio.Document est essentiel à la programmation de Visio. Il représente un fichier de dessin, de gabarit ou de modèle. Lorsque vous ouvrez un document Visio ou créez un document, vous créez un objet Microsoft.Office.Interop.Visio.Document, qui est ajouté à la collection Microsoft.Office.Interop.Visio.Documents de l'objet Microsoft.Office.Interop.Visio.Application.  
  
 Le document qui a le focus est appelé le document actif. Il est représenté par la propriété Microsoft.Office.Interop.Visio.Application.ActiveDocument de l'objet Microsoft.Office.Interop.Visio.Application.  
  
### Objet Page  
 L'objet Microsoft.Office.Interop.Visio.Page représente la zone de dessin d'une page de premier plan ou d'arrière\-plan. Vous pouvez utiliser la propriété Microsoft.Office.Interop.Visio.Page.Background pour déterminer si une page est une page de premier plan ou d'arrière\-plan.  
  
 Pour créer des formes, vous pouvez utiliser les méthodes qui incluent les méthodes Microsoft.Office.Interop.Visio.Page.DrawSpline et Microsoft.Office.Interop.Visio.Page.DrawOval. En outre, vous pouvez récupérer des formes de base de gabarits et placer ces formes sur une page à l'aide des méthodes Microsoft.Office.Interop.Visio.Page.Drop ou Microsoft.Office.Interop.Visio.Page.DropMany.  
  
## Utilisation de la documentation du modèle objet Visio  
 Pour obtenir des informations complètes sur le modèle objet Visio, vous pouvez vous reporter à la référence du modèle objet Visio VBA. La documentation du modèle objet VBA présente le modèle objet Visio tel qu'il est exposé au code VBA \(Visual Basic pour Applications\). Pour plus d’informations, consultez [Référence du modèle objet Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Visio. Par exemple, l'objet Document de la documentation de référence du modèle objet VBA correspond au type Microsoft.Office.Interop.Visio.Document de l'assembly PIA Visio. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans documentation de référence en Visual Basic ou Visual C\# pour pouvoir les utiliser dans un projet de complément VSTO Visio créé à l'aide de Visual Studio.  
  
> [!NOTE]  
>  À ce stade, il n'existe aucune documentation de référence pour l'assembly PIA Visio.  
  
 Pour obtenir des exemples de code associés et des outils supplémentaires de création de solutions Visio, consultez le [Kit de développement logiciel Visio 2010](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### Types supplémentaires dans les assemblys PIA  
 Vous pouvez trouver des types dans les assemblys PIA qui ne sont pas visibles par VBA en raison des différences d'implémentation. VBA fournit une vue du modèle objet Visio qui inclut uniquement les objets et les membres que vous pouvez utiliser directement. Les assemblys PIA exposent le même modèle objet, mais incluent également les autres interfaces, classes et membres qui convertissent les objets du modèle objet COM en code managé. Ces éléments supplémentaires ne sont pas destinés à être utilisés directement dans votre code.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des classes et des interfaces dans les assemblys PIA \(Primary Interop Assembly\) d’Office](http://go.microsoft.com/fwlink/?LinkId=189592) et [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Utilisation de documents Visio](../vsto/working-with-visio-documents.md)   
 [Utilisation de formes Visio](../vsto/working-with-visio-shapes.md)  
  
  