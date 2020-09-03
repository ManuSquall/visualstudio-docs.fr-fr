---
title: Propriétés de document personnalisées dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708967"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Propriétés de document personnalisées dans un service de langage hérité
Les propriétés du document peuvent être affichées dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fenêtre **Propriétés** . Les langages de programmation n’ont généralement pas de propriétés associées à des fichiers sources individuels. Toutefois, XML prend en charge les propriétés de document qui affectent l’encodage, le schéma et la feuille de style.

## <a name="discussion"></a>Discussion
 Si votre langue a besoin de propriétés de document personnalisées, vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe et implémenter les propriétés nécessaires sur votre classe dérivée.

 En outre, les propriétés de document sont généralement stockées dans le fichier source lui-même. Cela nécessite que le service de langage analyse les informations de propriété du fichier source pour les afficher dans la fenêtre **Propriétés** et pour mettre à jour le fichier source quand une modification est apportée aux propriétés du document dans la fenêtre **Propriétés** .

## <a name="customize-the-documentproperties-class"></a>Personnaliser la classe DocumentProperties
 Pour prendre en charge les propriétés de document personnalisées, vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe et ajouter le nombre de propriétés dont vous avez besoin. Vous devez également fournir des attributs utilisateur pour les organiser dans l’affichage de la fenêtre **Propriétés** . Si une propriété a uniquement un `get` accesseur, elle est affichée en lecture seule dans la fenêtre **Propriétés** . Si une propriété possède des `get` `set` accesseurs et, la propriété peut également être mise à jour dans la fenêtre **Propriétés** .

### <a name="example"></a>Exemple
 Voici un exemple de classe dérivée de <xref:Microsoft.VisualStudio.Package.DocumentProperties> , qui présente deux propriétés, `Filename` et `Description` . Quand une propriété est mise à jour, une méthode personnalisée sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe est appelée pour écrire la propriété dans le fichier source.

```csharp
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

## <a name="instantiate-the-custom-documentproperties-class"></a>Instancier la classe personnalisée DocumentProperties
 Pour instancier votre classe de propriétés de document personnalisée, vous devez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> méthode dans votre version de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une seule instance de votre <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe.

### <a name="example"></a>Exemple

```csharp
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

## <a name="properties-in-the-source-file"></a>Propriétés dans le fichier source
 Étant donné que les propriétés de document sont généralement spécifiques au fichier source, les valeurs sont stockées dans le fichier source lui-même. Cela nécessite la prise en charge de l’analyseur de langage ou du scanneur pour définir ces propriétés. Par exemple, les propriétés d’un document XML sont stockées sur le nœud racine. Les valeurs du nœud racine sont modifiées lorsque les valeurs de la fenêtre **Propriétés** sont modifiées, et le nœud racine est mis à jour dans l’éditeur.

### <a name="example"></a>Exemple
 Cet exemple stocke les propriétés `Filename` et `Description` dans les deux premières lignes du fichier source, incorporées dans un en-tête de commentaire spécial, comme suit :

```
//!Filename = file.testext
//!Description = A sample file
```

 Cet exemple illustre les deux méthodes nécessaires pour récupérer et définir les propriétés de document à partir des deux premières lignes du fichier source, ainsi que la façon dont les propriétés sont mises à jour si l’utilisateur modifie directement le fichier source. La `SetPropertyValue` méthode dans l’exemple illustré ici est la même que celle qui est appelée à partir de la `TestDocumentProperties` classe, comme indiqué dans la section *Personnalisation de la classe DocumentProperties* .

 Cet exemple utilise le scanneur pour déterminer le type de jetons dans les deux premières lignes. Cet exemple est fourni à titre d’illustration uniquement. Une approche plus courante de cette situation consiste à analyser le fichier source dans ce qu’on appelle une arborescence d’analyse où chaque nœud de l’arborescence contient des informations sur un jeton particulier. Le nœud racine contient les propriétés du document.

```csharp
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

## <a name="see-also"></a>Voir aussi
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
