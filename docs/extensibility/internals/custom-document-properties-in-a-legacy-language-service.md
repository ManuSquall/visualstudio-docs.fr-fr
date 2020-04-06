---
title: Propriétés de documents personnalisées dans un service de langue héritée (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708967"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Propriétés de documents personnalisées dans un service linguistique hérité
Les propriétés de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documents peuvent être affichées dans la fenêtre **propriétés.** Les langages de programmation n’ont généralement pas de propriétés associées aux fichiers sources individuels. Cependant, XML prend en charge les propriétés de documents qui affectent l’encodage, le schéma et la feuille de style.

## <a name="discussion"></a>Discussions
 Si votre langue a besoin de propriétés <xref:Microsoft.VisualStudio.Package.DocumentProperties> de documents personnalisées, vous devez tirer une classe de la classe et implémenter les propriétés nécessaires sur votre classe dérivée.

 En outre, les propriétés de documents sont généralement stockées dans le fichier source lui-même. Cela exige que le service linguistique analyse les informations de propriété à partir du fichier source pour afficher dans la fenêtre **propriétés** et de mettre à jour le fichier source lorsqu’une modification est apportée aux propriétés du document dans la fenêtre **propriétés.**

## <a name="customize-the-documentproperties-class"></a>Personnaliser la classe DocumentProperties
 Pour prendre en charge les propriétés <xref:Microsoft.VisualStudio.Package.DocumentProperties> de documents personnalisées, vous devez tirer une classe de la classe et ajouter autant de propriétés que vous avez besoin. Vous devez également fournir des attributs utilisateur pour les organiser dans l’affichage de fenêtre **propriétés.** Si une propriété `get` n’a qu’un accessoir, elle est indiquée comme lue uniquement dans la fenêtre **Propriétés.** Si une propriété `get` `set` a à la fois et les accesseurs, la propriété peut également être mise à jour dans la fenêtre **propriétés.**

### <a name="example"></a>Exemple
 Voici un exemple de <xref:Microsoft.VisualStudio.Package.DocumentProperties>classe dérivée `Filename` `Description`de , montrant deux propriétés, et . Lorsqu’une propriété est mise à <xref:Microsoft.VisualStudio.Package.LanguageService> jour, une méthode personnalisée sur la classe est appelée à écrire la propriété au fichier source.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Instantané de la classe DocumentProperties personnalisée
 Pour instantanéiser votre classe de propriétés de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> documents personnalisées, <xref:Microsoft.VisualStudio.Package.LanguageService> vous devez passer outre <xref:Microsoft.VisualStudio.Package.DocumentProperties> à la méthode de votre version de la classe pour retourner une seule instance de votre classe.

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
 Étant donné que les propriétés de documents sont généralement spécifiques au fichier source, les valeurs sont stockées dans le fichier source lui-même. Cela nécessite un soutien de l’analyse de la langue ou du scanner pour définir ces propriétés. Par exemple, les propriétés d’un document XML sont stockées sur le nœud racine. Les valeurs du nœud de racine sont modifiées lorsque les valeurs de la fenêtre **Propriétés** sont modifiées, et le nœud racine est mis à jour dans l’éditeur.

### <a name="example"></a>Exemple
 Cet exemple stocke les propriétés `Filename` et `Description` dans les deux premières lignes du fichier source, intégré dans un en-tête de commentaire spécial, comme:

```
//!Filename = file.testext
//!Description = A sample file
```

 Cet exemple montre les deux méthodes nécessaires pour obtenir et définir les propriétés du document à partir des deux premières lignes du fichier source ainsi que la façon dont les propriétés sont mises à jour si l’utilisateur modifie directement le fichier source. La `SetPropertyValue` méthode dans l’exemple montré ici `TestDocumentProperties` est la même que celle appelée de la classe comme indiqué dans la *section Customizing the DocumentProperties class.*

 Cet exemple utilise le scanner pour déterminer le type de jetons dans les deux premières lignes. Cet exemple n’est qu’à des fins illustratives. Une approche plus typique de cette situation est d’analyser le fichier source dans ce qu’on appelle un arbre d’analyse où chaque nœud de l’arbre contient des informations sur un jeton particulier. Le nœud racine contiendrait les propriétés du document.

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
- [Caractéristiques du service linguistique hérité](../../extensibility/internals/legacy-language-service-features1.md)
