---
title: "CA3076 : L’exécution du Script XSLT non sécurisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bf7da81e41a00bd0d673e3522f944dc17a549c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076 : exécution non sécurisée de script XSLT
|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Si vous exécutez le [langage XSLT (Extensible Stylesheet Language Transformations)](https://support.microsoft.com/en-us/kb/313997) dans les applications .NET de manière non sécurisée, le processeur peut [résoudre les références URI non fiables](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) qui pourraient divulguer des informations sensibles à des personnes malveillantes, ce qui aboutirait à des attaques par déni de service et intersites.  
  
## <a name="rule-description"></a>Description de la règle  
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) est une norme W3C (World Wide Web Consortium) pour la transformation des données XML. XSLT est généralement utilisé pour écrire des feuilles de style pour transformer des données XML sous d’autres formats tels que HTML, un texte de longueur fixe, un texte délimité par des virgules ou un autre format XML. Bien qu’il soit interdit par défaut, vous pouvez choisir de l’activer pour votre projet.  
  
 Pour garantir que vous ne vous exposez pas aux attaques, cette règle se déclenche chaque fois que XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> reçoit des instances de combinaisons non sécurisées de <xref:System.Xml.Xsl.XsltSettings> et <xref:System.Xml.XmlResolver>, ce qui permet le traitement de scripts malveillants.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
  
-   Remplacez l’argument XsltSettings non sécurisé par XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou par une instance qui a désactivé l’exécution de script et de fonction document.  
  
-   Remplacez l’argument <xref:System.Xml.XmlResolver> par la valeur null ou une instance de <xref:System.Xml.XmlSecureResolver> .  
  
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