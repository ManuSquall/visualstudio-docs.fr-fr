---
title: Méthodes de débogage du code XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f6f4a1ce60f04bcea6e21b52db9347a95292dab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592852"
---
# <a name="debugging-xslt"></a>Débogage XSLT

Vous pouvez déboguer du code XSLT dans Visual Studio. Le débogueur XSLT prend en charge la définition de points d’arrêt, l’affichage des États d’exécution XSLT, etc. Le débogueur XSLT peut être utilisé pour déboguer des feuilles de style XSLT ou des applications XSLT.

Vous pouvez exécuter le code ligne par ligne en effectuant un pas à pas détaillé, pas à pas principal ou en sortant du code. Les commandes permettant d’utiliser la fonctionnalité d’exécution pas à pas du code du débogueur XSLT sont les mêmes que celles des autres débogueurs Visual Studio.

Une fois le débogage lancé, le débogueur XSLT ouvre des fenêtres pour afficher le document d'entrée et la sortie XSLT.

> [!NOTE]
> Le débogueur XSLT n’est disponible que dans les éditions Professional et Enterprise de Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Déboguer à partir de l’éditeur XML

Vous pouvez démarrer le débogueur quand une feuille de style ou un fichier XML d’entrée est ouvert dans l’éditeur. Cela vous permet de déboguer au fur et à mesure que vous concevez la feuille de style.

1. Ouvrez la feuille de style ou le fichier XML dans Visual Studio.

1. Sélectionnez **Démarrer le débogage XSLT** dans le menu **XML** ou appuyez sur **ALT**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Déboguer à partir d’une application qui utilise XSLT

Vous pouvez effectuer un pas à pas détaillé dans XSLT lors du débogage d’une application. Quand vous appuyez sur **F11** sur un appel <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, le débogueur peut effectuer un pas à pas détaillé dans le code XSLT.

> [!NOTE]
> L'exécution d'un pas à pas détaillé de XSLT à partir de la classe <xref:System.Xml.Xsl.XslTransform> n'est pas prise en charge. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le seul processeur XSLT prenant en charge l'exécution d'un pas à pas détaillé du code XSLT pendant le débogage.

### <a name="to-start-debugging-an-xslt-application"></a>Pour commencer le débogage d'une application XSLT

1. Lors de l'instanciation de l'objet <xref:System.Xml.Xsl.XslCompiledTransform>, définissez le paramètre `enableDebug` sur `true` dans votre code. Le processeur XSLT crée alors des informations de débogage lors de la compilation du code.

1. Appuyez sur **F11** pour effectuer un pas à pas détaillé dans le code XSLT.

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
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Profileur XSLT

Le [profileur XSLT](../xml-tools/xslt-profiler.md) est un outil qui permet aux développeurs de mesurer, d’évaluer et de cibler les problèmes liés aux performances dans le code XSLT en créant des rapports détaillés sur les performances XSLT. Pour plus d’informations, consultez [XSLT Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Premier aperçu du débogueur Visual Studio](../debugger/debugger-feature-tour.md)
- [Concepts de base du débogage : points d’arrêt](../debugger/using-breakpoints.md)
