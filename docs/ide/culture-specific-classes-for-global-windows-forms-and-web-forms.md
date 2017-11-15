---
title: "Classes spécifiques à la culture pour les Windows Forms et les Web Forms globaux | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1864d3bd07906d5bd7413689c912e0a3c7ede036
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Classes spécifiques à la culture pour les Windows Forms et les Web Forms globaux
Chaque culture a ses propres conventions d’affichage des dates, des heures, des nombres, des devises et d’autres informations. L’espace de noms <xref:System.Globalization> contient des classes qui peuvent être utilisées pour modifier la façon dont les valeurs spécifiques à une culture sont affichées, comme <xref:System.Globalization.DateTimeFormatInfo>, **Calendar** et <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Utilisation du paramètre de culture  
 Mais la plupart du temps, vous utilisez le paramètre de culture stocké dans l’application ou dans le panneau de configuration **Options régionales** pour déterminer automatiquement les conventions au moment de l’exécution et mettre en forme les informations en conséquence. Pour plus d’informations sur la définition de la culture, consultez [Comment : définir la culture et la culture de l’interface utilisateur pour la globalisation de Windows Forms](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) ou [Comment : définir la culture et la culture de l’interface utilisateur pour la globalisation des pages web ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Les classes qui mettent en forme automatiquement les informations en fonction du paramètre de culture sont appelées des classes spécifiques à une culture. <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> et <xref:System.String.Format%2A?displayProperty=fullName> sont des méthodes spécifiques à une culture. `MonthName` et `WeekDayName` sont des méthodes spécifiques à une culture (dans le langage Visual Basic).  
  
 Par exemple, le code suivant montre comment vous pouvez utiliser la méthode <xref:System.IFormattable.ToString%2A> pour mettre en forme la devise pour la culture active :  
  
```vb  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```csharp  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 Si la culture est définie sur « fr-FR », vous voyez ceci dans la fenêtre de sortie :  
  
 `100,00`  
  
 Si la culture est définie sur « en-US », vous voyez ceci dans la fenêtre de sortie :  
  
 `$100.00`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)