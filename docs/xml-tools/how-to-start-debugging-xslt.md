---
title: 'Procédure : démarrage du débogage XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 9e3251d83361623aea0c0a54a2752c97b06a66f8
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561864"
---
# <a name="how-to-start-debugging-xslt"></a>Procédure : Démarrer le débogage XSLT

Le débogueur XSLT permet de déboguer une feuille de style XSLT ou une application XSLT. Lors du débogage, vous pouvez exécuter le code ligne par ligne (pas à pas détaillé, pas à pas principal ou pas à pas sortant). Les commandes permettant d'utiliser la fonctionnalité d'exécution du code pas à pas dans le débogueur XSLT sont identiques à celles des autres débogueurs Visual Studio. Une fois le débogage lancé, le débogueur XSLT ouvre des fenêtres pour afficher le document d'entrée et la sortie XSLT.

## <a name="xml-editor"></a>Éditeur XML

Vous pouvez démarrer le débogueur à partir de l'éditeur XML. Vous pouvez ainsi déboguer une feuille de style à mesure que vous la concevez.

### <a name="to-start-debugging-from-a-style-sheet"></a>Pour commencer le débogage à partir d'une feuille de style

1. Ouvrez la feuille de style dans l'éditeur XML.

1. Sélectionnez **débogage XSLT** à partir de la **XML** menu.

### <a name="to-start-debugging-from-an-xml-input-document"></a>Pour commencer le débogage à partir d'un document d'entrée XML

1. Ouvrez le document XML dans l'éditeur XML.

1. Sélectionnez **débogage XSLT** à partir de la **XML** menu.

## <a name="xslt-from-other-languages"></a>XSLT à partir d’autres langages

Vous pouvez également exécuter un pas à pas détaillé de XSLT pendant le débogage d'une application. Si vous appuyez sur F11 lors d'un appel à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, le débogueur peut exécuter un pas à pas détaillé du code XSLT.

> [!NOTE]
> L'exécution d'un pas à pas détaillé de XSLT à partir de la classe <xref:System.Xml.Xsl.XslTransform> n'est pas prise en charge. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le seul processeur XSLT prenant en charge l'exécution d'un pas à pas détaillé du code XSLT pendant le débogage.

### <a name="to-start-debugging-an-xslt-application"></a>Pour commencer le débogage d'une application XSLT

1. Lors de l'instanciation de l'objet <xref:System.Xml.Xsl.XslCompiledTransform>, définissez le paramètre `enableDebug` sur `true` dans votre code.

     Le processeur XSLT crée alors des informations de débogage lors de la compilation du code.

1. Appuyez sur F11 pour exécuter un pas à pas détaillé du code XSLT.

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
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
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

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)   