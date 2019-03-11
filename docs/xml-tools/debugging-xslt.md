---
title: Façons de déboguer le code XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 23e108e476bfa9cb3ce699a16c77eb3520ed4785
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526384"
---
# <a name="debugging-xslt"></a>Débogage XSLT

Vous pouvez déboguer le code XSLT dans Visual Studio. Le fichier XSLT prend en charge des points d’arrêt, l’affichage des États d’exécution de XSLT du débogueur et ainsi de suite. Le débogueur XSLT peut être utilisé pour déboguer des feuilles de style XSLT ou les applications XSLT.

Vous pouvez exécuter le code ligne par ligne à la fois par détaillé, pas à pas principal ou pas à pas sortant du code. Les commandes pour l’utilisation de la fonctionnalité d’exécution de code du débogueur XSLT sont que les mêmes que celles pour le Visual Studio débogueurs.

Une fois le débogage lancé, le débogueur XSLT ouvre des fenêtres pour afficher le document d'entrée et la sortie XSLT.

> [!NOTE]
> Le débogueur XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Déboguer à partir de l’éditeur XML

Vous pouvez démarrer le débogueur lorsque vous avez une feuille de style ou un fichier XML d’entrée ouvrir dans l’éditeur. Cela vous permet de déboguer comme vous concevez la feuille de style.

1. Ouvrez la feuille de style ou d’un fichier XML dans Visual Studio.

1. Sélectionnez **démarrer le débogage XSLT** à partir de la **XML** menu ou appuyez sur **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Déboguer à partir d’une application qui utilise XSLT

Vous pouvez entrer dans XSLT pendant le débogage d’une application. Quand vous appuyez sur **F11** sur un <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> appel, le débogueur peut accéder dans le code XSLT.

> [!NOTE]
> L'exécution d'un pas à pas détaillé de XSLT à partir de la classe <xref:System.Xml.Xsl.XslTransform> n'est pas prise en charge. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le seul processeur XSLT prenant en charge l'exécution d'un pas à pas détaillé du code XSLT pendant le débogage.

### <a name="to-start-debugging-an-xslt-application"></a>Pour commencer le débogage d'une application XSLT

1. Lors de l'instanciation de l'objet <xref:System.Xml.Xsl.XslCompiledTransform>, définissez le paramètre `enableDebug` sur `true` dans votre code. Le processeur XSLT crée alors des informations de débogage lors de la compilation du code.

1. Appuyez sur **F11** à pas détaillé dans le code XSLT.

   La feuille de style XSLT est chargée dans une nouvelle fenêtre de document et le débogueur XSLT démarre.

   Vous pouvez aussi ajouter un point d'arrêt à la feuille de style et exécuter votre application.

### <a name="example"></a>Exemple

Voici un exemple de programme XSLT C#. Il indique comment activer le débogage XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Générateur de profils XSLT

Le [Générateur de profils XSLT](../xml-tools/xslt-profiler.md) est un outil qui permet aux développeurs de mesurer, évaluer et cibler les problèmes de performances dans le code XSLT en créant des rapports de performances XSLT détaillés. Pour plus d’informations, consultez [Générateur de profils XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Tout d’abord examiner le débogueur Visual Studio](../debugger/debugger-feature-tour.md)
- [Principes de base pour le débogage : Points d’arrêt](../debugger/using-breakpoints.md)