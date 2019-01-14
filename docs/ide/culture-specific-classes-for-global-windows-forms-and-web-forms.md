---
title: Classes spécifiques à la culture pour les Windows Forms et les Web Forms globaux
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cb0215c27b8d1fb09f54bc8590d24b99403670f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989959"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Classes spécifiques à la culture pour les Windows Forms et les Web Forms globaux

Chaque culture a ses propres conventions d’affichage des dates, des heures, des nombres, des devises et d’autres informations. L’espace de noms <xref:System.Globalization> contient des classes qui peuvent être utilisées pour modifier la façon dont les valeurs spécifiques à une culture sont affichées, par exemple :
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Utilisation du paramètre de culture

Utilisez le paramètre de culture stocké dans l’application ou dans **Options régionales** du Panneau de configuration pour déterminer les conventions de culture au moment de l’exécution, et mettre en forme les informations de manière appropriée. Pour plus d’informations sur la définition de la culture, consultez [Guide pratique pour définir la culture et la culture d’interface utilisateur pour la globalisation des pages web ASP.NET](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Les classes qui mettent en forme automatiquement les informations en fonction du paramètre de culture sont appelées des classes *spécifiques à une culture*. Les méthodes spécifiques à une culture sont
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

`MonthName` et `WeekDayName` sont des méthodes spécifiques à une culture (dans le langage Visual Basic).

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

Si la culture a la valeur « fr-FR », vous voyez ce qui suit dans la fenêtre Sortie :

`100,00`

Si la culture a la valeur « en-US », vous voyez ce qui suit dans la fenêtre Sortie :

`$100.00`

## <a name="see-also"></a>Voir aussi

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)