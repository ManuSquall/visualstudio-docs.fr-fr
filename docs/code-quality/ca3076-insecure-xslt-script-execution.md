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
ms.workload: multiple
ms.openlocfilehash: 09cf5533bff2eb2254f3ca70d4dea275c9354201
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076 : exécution non sécurisée de script XSLT
|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Category|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Si vous exécutez [Stylesheets Language Transformations XSLT (Extensible)](https://support.microsoft.com/en-us/kb/313997) dans les applications .NET de manière non sécurisée, le processeur peut résoudre les références URI non fiables qui pourraient divulguer des informations sensibles à des personnes malveillantes, conduisant à Attaques par déni de Service et intersites.  
  
## <a name="rule-description"></a>Description de la règle  
 **XSLT** est une norme World Wide Web Consortium (W3C) pour la transformation des données XML. XSLT est généralement utilisé pour écrire des feuilles de style pour transformer des données XML sous d’autres formats tels que HTML, un texte de longueur fixe, un texte délimité par des virgules ou un autre format XML. Bien qu’il soit interdit par défaut, vous pouvez choisir de l’activer pour votre projet.  
  
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