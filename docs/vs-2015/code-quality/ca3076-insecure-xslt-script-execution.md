---
title: 'CA3076 : exécution du script XSLT non sécurisée | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545117"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076 : Exécution non sécurisée de script XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Si vous exécutez le [langage XSLT (Extensible Stylesheet Language Transformations)](https://support.microsoft.com/kb/313997) dans les applications .net de manière non sécurisée, le processeur peut [résoudre les références URI non fiables](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) qui pourraient divulguer des informations sensibles aux attaquants, entraînant des attaques par déni de service et intersites.

## <a name="rule-description"></a>Description de la règle
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) est une norme W3C (World Wide Web Consortium) pour la transformation des données XML. XSLT est généralement utilisé pour écrire des feuilles de style pour transformer des données XML sous d’autres formats tels que HTML, un texte de longueur fixe, un texte délimité par des virgules ou un autre format XML. Bien qu’il soit interdit par défaut, vous pouvez choisir de l’activer pour votre projet.

 Pour vous assurer que vous n’exposez pas de surface d’attaque, cette règle se déclenche chaque fois que XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> reçoit des instances de combinaisons non sécurisées de <xref:System.Xml.Xsl.XsltSettings> et <xref:System.Xml.XmlResolver> , ce qui permet le traitement de scripts malveillants.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Remplacez l’argument XsltSettings non sécurisé par XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou avec une instance qui a désactivé la fonction de document et l’exécution du script.

- Remplacez l’argument <xref:System.Xml.XmlResolver> par la valeur null ou une instance de <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Sauf si vous êtes sûr que l’entrée provient d’une source fiable, ne supprimez aucune règle de cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Solution

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Violation

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```
