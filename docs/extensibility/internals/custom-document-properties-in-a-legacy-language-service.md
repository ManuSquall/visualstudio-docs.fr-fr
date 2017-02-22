---
title: "Propri&#233;t&#233;s de Document personnalis&#233;es dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés de document personnalisées, les services de langage (framework package managé)"
  - "propriétés de document personnalisées"
  - "services de langage (framework package managé), les propriétés de document personnalisées"
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Propri&#233;t&#233;s de Document personnalis&#233;es dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les propriétés de document peuvent être affichées dans la fenêtre de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**Propriétés** .  Les langages de programmation en général n'ont pas de propriétés associées à des fichiers sources. Toutefois, les propriétés de document de prises en charge XML qui affectent l'encodage, le schéma, et la feuille de style.  
  
## Discussion  
 Si votre langage a besoin de propriétés de document personnalisées, vous devez dériver une classe de la classe d' <xref:Microsoft.VisualStudio.Package.DocumentProperties> et implémenter des propriétés nécessaires sur votre classe dérivée.  
  
 En outre, les propriétés du document sont généralement stockées dans le fichier source lui\-même.  Cela exige du service de langage pour analyser les informations de propriété du fichier source à afficher dans la fenêtre de **Propriétés** et pour mettre à jour le fichier source lorsqu'une modification est apportée aux propriétés de document de la fenêtre de **Propriétés** .  
  
## personnaliser la classe de DocumentProperties  
 Pour prendre en charge des propriétés de document personnalisées, vous devez dériver une classe de la classe d' <xref:Microsoft.VisualStudio.Package.DocumentProperties> et ajouter autant de propriétés comme vous avez besoin.  Vous devez également fournir des attributs d'utilisateur pour les organiser dans l'affichage de la fenêtre de **Propriétés** .  Si une propriété n'a qu'un accesseur d' `get` , elle est affichée en lecture seule dans la fenêtre de **Propriétés** .  Si une propriété a `get` les accesseurs d' `set` , la propriété peut également être mise à jour dans la fenêtre de **Propriétés** .  
  
### Exemple  
 Voici une classe d'exemple dérivée d' <xref:Microsoft.VisualStudio.Package.DocumentProperties>, en affichant deux propriétés, les noms de fichiers et descriptions.  Lorsqu'une propriété est mise à jour, une méthode personnalisée pour la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> est appelée pour écrire la propriété au fichier source.  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## instancier la classe personnalisée de DocumentProperties  
 Pour instancier votre classe de propriétés de document personnalisées, vous devez substituer la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> dans votre version de la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> pour retourner une seule instance de votre classe d' <xref:Microsoft.VisualStudio.Package.DocumentProperties> .  
  
### Exemple  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## propriétés dans le fichier source  
 Étant donné que les propriétés de document sont généralement spécifiques au fichier source, les valeurs sont stockées dans le fichier source lui\-même.  Cela requiert la prise en charge de l'analyseur ou de scanneur de langage pour définir ces propriétés.  Par exemple, les propriétés d'un document XML sont à la racine nœud enregistré.  Le nœud de valeurs à la racine sont modifiés lorsque les valeurs de fenêtre de **Propriétés** sont modifiées, et le nœud racine est mis à jour dans l'éditeur.  
  
### Exemple  
 Cet exemple enregistre les propriétés « nomfichier » et « description » dans les deux premières lignes du fichier source, incorporées dans un en\-tête spécial de commentaire, comme suit :  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 Cet exemple indique que les deux méthodes nécessaires pour obtenir et définir les propriétés de document les deux premières lignes du fichier source et comment les propriétés sont mises à jour si l'utilisateur modifie le fichier source directement.  La méthode d' `SetPropertyValue` dans l'exemple présenté ici est la même appelée à partir de la classe d' `TestDocumentProperties` comme indiqué dans la section « personnalisation de DocumentProperties classe ».  
  
 Cet exemple utilise le scanner pour déterminer le type de jetons dans les deux premières lignes.  Cet exemple est dans des fins de illustration uniquement.  Une approche plus courant à cette situation est d'analyser le fichier source en ce qu'on appelle arborescence d'analyser où chaque nœud de l'arborescence contient des informations sur un jeton donné.  Le nœud racine contient les propriétés du document.  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Voir aussi  
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)