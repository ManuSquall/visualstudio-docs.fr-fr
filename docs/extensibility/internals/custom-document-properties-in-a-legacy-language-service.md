---
title: Propriétés de Document personnalisées dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98402a61629b48b25a8636aaf6a912e89c283951
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605833"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Propriétés de document personnalisées dans un service de langage hérité
Propriétés de document peuvent être affichées dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriétés** fenêtre. Langages de programmation ne disposent généralement pas de propriétés associées aux fichiers sources individuels. Toutefois, XML prend en charge les propriétés de document qui affectent l’encodage, schéma et la feuille de style.

## <a name="discussion"></a>Discussion
 Si votre langage a besoin de propriétés de document personnalisées, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe et implémenter les propriétés nécessaires sur votre classe dérivée.

 En outre, les propriétés de document sont généralement stockées dans le fichier source lui-même. Cela nécessite le service de langage pour analyser les informations de propriété à partir du fichier source à afficher dans le **propriétés** fenêtre et mettre à jour le fichier source lorsqu’une modification est apportée aux propriétés de document dans le  **Propriétés** fenêtre.

## <a name="customize-the-documentproperties-class"></a>Personnaliser la classe DocumentProperties
 Pour prendre en charge les propriétés de document personnalisées, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> et ajouter toutes les propriétés que vous avez besoin. Vous devez également fournir des attributs de l’utilisateur pour les organiser dans le **propriétés** affichage de la fenêtre. Si une propriété a uniquement un `get` accesseur, il est indiqué comme étant en lecture seule dans le **propriétés** fenêtre. Si une propriété dispose à la fois `get` et `set` accesseurs de la propriété peut également être mis à jour dans le **propriétés** fenêtre.

### <a name="example"></a>Exemple
 Voici un exemple de classe dérivé <xref:Microsoft.VisualStudio.Package.DocumentProperties>, affichant les deux propriétés, `Filename` et `Description`. Lorsqu’une propriété est mis à jour, une méthode personnalisée sur le <xref:Microsoft.VisualStudio.Package.LanguageService> classe est appelée pour écrire la propriété dans le fichier source.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Instancier la classe DocumentProperties personnalisée
 Pour instancier votre classe de propriétés de document personnalisées, vous devez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> méthode dans votre version de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une instance unique de votre <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe.

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
 Étant donné que les propriétés de document sont généralement spécifiques au fichier source, les valeurs sont stockées dans le fichier source lui-même. Cela nécessite la prise en charge à partir de l’Analyseur de langage ou le scanneur pour définir ces propriétés. Par exemple, les propriétés d’un document XML sont stockées sur le nœud racine. Les valeurs sur le nœud racine sont modifiés lorsque la **propriétés** les valeurs sont modifiées et le nœud racine est mis à jour dans l’éditeur.

### <a name="example"></a>Exemple
 Cet exemple stocke les propriétés `Filename` et `Description` dans les deux premières lignes du fichier source, incorporé dans un en-tête de commentaires spéciaux, comme :

```
//!Filename = file.testext
//!Description = A sample file
```

 Cet exemple montre les deux méthodes nécessaires pour obtenir et définir les propriétés de document dans les deux premières lignes du fichier source, ainsi que la manière dont les propriétés sont mises à jour si l’utilisateur modifie le fichier source directement. Le `SetPropertyValue` méthode dans l’exemple présenté ici est le même qu’une appelée à partir du `TestDocumentProperties` classe comme indiqué dans le *personnalisation de la classe DocumentProperties* section.

 Cet exemple utilise le moteur d’analyse pour déterminer le type de jetons dans les deux premières lignes. Cet exemple est uniquement à des fins d’illustration. Une approche plus courant à cette situation consiste à analyser le fichier source dans ce que l'on appelle une arborescence d’analyse où chaque nœud de l’arborescence contient des informations sur un jeton donné. Le nœud racine contient les propriétés de document.

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
- [Fonctionnalités de service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)