---
title: "CA3076 : L’exécution du Script XSLT non sécurisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66d415b792558dce91de0205ee688fecb5caa182
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076 : exécution non sécurisée de script XSLT

|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Category|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  

## <a name="cause"></a>Cause

Si vous exécutez le langage XSLT (Extensible Stylesheet Language Transformations) dans les applications .NET de manière non sécurisée, le processeur peut résoudre les références URI non fiables qui pourraient divulguer des informations sensibles à des personnes malveillantes, ce qui aboutirait à des attaques par déni de service et intersites. Pour plus d’informations, consultez [XSLT sécurité Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Description de la règle

**XSLT** est une norme World Wide Web Consortium (W3C) pour la transformation des données XML. XSLT est généralement utilisé pour écrire des feuilles de style pour transformer des données XML sous d’autres formats tels que HTML, un texte de longueur fixe, un texte délimité par des virgules ou un autre format XML. Bien qu’il soit interdit par défaut, vous pouvez choisir de l’activer pour votre projet.

Pour garantir que vous ne vous exposez pas aux attaques, cette règle se déclenche chaque fois que XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> reçoit des instances de combinaisons non sécurisées de <xref:System.Xml.Xsl.XsltSettings> et <xref:System.Xml.XmlResolver>, ce qui permet le traitement de scripts malveillants.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Remplacez l’argument XsltSettings non sécurisé par XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou par une instance qui a désactivé l’exécution de script et de fonction document.

- Remplacez l’argument <xref:System.Xml.XmlResolver> par la valeur null ou une instance de <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Sauf si vous êtes sûr que l’entrée provient d’une source fiable, ne supprimez aucune règle de cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violationmdashuses-xsltsettingstrustedxslt"></a>Violation&mdash;utilise XsltSettings.TrustedXslt

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

### <a name="solutionmdashuse-xsltsettingsdefault"></a>Solution&mdash;utiliser XsltSettings.Default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Violation de&mdash;d’exécution de script et de fonction ne désactivée pas de document

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solution&mdash;désactiver l’exécution du script et de fonction document

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

## <a name="see-also"></a>Voir aussi

[Considérations de sécurité XSLT (Guide .NET)](/dotnet/standard/data/xml/xslt-security-considerations)