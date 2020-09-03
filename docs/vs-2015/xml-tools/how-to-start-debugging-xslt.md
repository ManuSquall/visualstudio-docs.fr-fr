---
title: 'Procédure : démarrer le débogage de XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656331"
---
# <a name="how-to-start-debugging-xslt"></a>Procédure : démarrer le débogage XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur XSLT permet de déboguer une feuille de style XSLT ou une application XSLT. Lors du débogage, vous pouvez exécuter le code ligne par ligne (pas à pas détaillé, pas à pas principal ou pas à pas sortant). Les commandes permettant d'utiliser la fonctionnalité d'exécution du code pas à pas dans le débogueur XSLT sont identiques à celles des autres débogueurs Visual Studio. Une fois le débogage lancé, le débogueur XSLT ouvre des fenêtres pour afficher le document d'entrée et la sortie XSLT.

## <a name="xml-editor"></a>Éditeur XML
 Vous pouvez démarrer le débogueur à partir de l'éditeur XML. Vous pouvez ainsi déboguer une feuille de style à mesure que vous la concevez.

#### <a name="to-start-debugging-from-a-style-sheet"></a>Pour commencer le débogage à partir d'une feuille de style

1. Ouvrez la feuille de style dans l'éditeur XML.

2. Sélectionnez **Déboguer xsl** dans le menu **XML** .

#### <a name="to-start-debugging-from-an-xml-input-document"></a>Pour commencer le débogage à partir d'un document d'entrée XML

1. Ouvrez le document XML dans l'éditeur XML.

2. Sélectionnez **Déboguer xsl** dans le menu **XML** .

## <a name="xslt-from-other-languages"></a>XSLT à partir d'autres langages
 Vous pouvez également exécuter un pas à pas détaillé de XSLT pendant le débogage d'une application. Si vous appuyez sur F11 lors d'un appel à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, le débogueur peut exécuter un pas à pas détaillé du code XSLT.

> [!NOTE]
> L'exécution d'un pas à pas détaillé de XSLT à partir de la classe <xref:System.Xml.Xsl.XslTransform> n'est pas prise en charge. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le seul processeur XSLT prenant en charge l'exécution d'un pas à pas détaillé du code XSLT pendant le débogage.

#### <a name="to-start-debugging-an-xslt-application"></a>Pour commencer le débogage d'une application XSLT

1. Lors de l'instanciation de l'objet <xref:System.Xml.Xsl.XslCompiledTransform>, définissez le paramètre `enableDebug` sur `true` dans votre code.

     Le processeur XSLT crée alors des informations de débogage lors de la compilation du code.

2. Appuyez sur F11 pour exécuter un pas à pas détaillé du code XSLT.

     La feuille de style XSLT est chargée dans une nouvelle fenêtre de document et le débogueur XSLT démarre.

     Vous pouvez aussi ajouter un point d'arrêt à la feuille de style et exécuter votre application.

### <a name="example"></a>Exemple
 Voici un exemple de programme XSLT C#. Il indique comment activer le débogage XSLT.

```
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
 [Procédure pas à pas : déboguer une](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) [vue d’ensemble du code](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) de feuille de style XSLT
