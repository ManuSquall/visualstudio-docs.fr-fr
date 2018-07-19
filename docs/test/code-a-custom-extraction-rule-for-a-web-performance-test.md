---
title: Codage d’une règle d’extraction personnalisée pour un test de performances web dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 02fd481455c5198a1d8ae0828072f8085d1d027a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31966158"
---
# <a name="coding-a-custom-extraction-rule-for-a-web-performance-test"></a>Codage d'une règle d'extraction personnalisée pour un test de performances de site Web

Vous pouvez créer vos propres règles d'extraction. Pour cela, vous dérivez vos propres règles à partir d'une classe de règles d'extraction. Les règles d'extraction dérivent de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> Il est également possible de créer vos propres règles de validation personnalisées. Pour plus d’informations, consultez [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md).

## <a name="to-create-a-custom-extraction-rule"></a>Pour créer une règle d'extraction personnalisée

1.  Ouvrez un projet de test qui contient un test de performances de site web.

2.  (Facultatif) Créez un projet Bibliothèque de classes distinct dans lequel stocker votre règle d'extraction.

    > [!IMPORTANT]
    > Vous pouvez créer la classe dans le projet qui contient vos tests. Toutefois, si vous souhaitez réutiliser la règle, il est préférable de créer un projet de bibliothèque de classes distinct pour la stocker. Si vous créez un projet séparé, vous devez compléter les étapes facultatives dans cette procédure.

3.  (Facultatif) Dans le projet Bibliothèque de classes, ajoutez une référence à Microsoft.VisualStudio.QualityTools.WebTestFramework dll.

4.  Créez une classe qui dérive de la classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Implémentez les membres <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5.  (Facultatif) Générez le nouveau projet de bibliothèque de classes.

6.  (Facultatif) Dans le projet de test, ajoutez une référence au projet Bibliothèque de classes qui contient la règle d'extraction personnalisée.

7.  Dans le projet de test, ouvrez un test de performances web dans l’**éditeur de test de performances web**.

8.  Pour ajouter la règle d’extraction personnalisée, cliquez avec le bouton droit sur une requête de test de performances web, puis sélectionnez **Ajouter une règle d’extraction**.

     La boîte de dialogue **Ajouter une règle d’extraction** s’affiche. Votre règle de validation personnalisée apparaît dans la liste **Sélectionner une règle** avec les règles de validation prédéfinies. Sélectionnez votre règle d’extraction personnalisée, puis choisissez **OK**.

9. Exécutez votre test de performances de site web.

## <a name="example"></a>Exemple

Le code suivant illustre une implémentation d'une règle d'extraction personnalisée. Cette règle d'extraction extrait la valeur d'un champ d'entrée spécifié. Utilisez cet exemple comme point de départ pour vos propres règles d'extraction personnalisées.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

La méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> contient la fonctionnalité principale d'une règle d'extraction. La méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> de l'exemple précédent prend un <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> qui fournit la réponse générée par la demande couverte par cette règle d'extraction. La réponse contient un <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> qui contient toutes les balises dans la réponse. Les balises d'entrées sont éliminées du <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> par filtrage. Chaque étiquette d’entrée est examinée pour y détecter la présence d’un attribut appelé `name` dont la valeur est égale à la valeur utilisateur de la propriété `Name`. Si une étiquette avec l’attribut correspondant est trouvée, une tentative d’extraction de la valeur contenue dans l’attribut `value` est effectuée (si une valeur d’attribut existe). Si une valeur d’attribut existe, le nom et la valeur de l’étiquette sont extraits et ajoutés au contexte de test de performances de site Web. La règle d'extraction est passée.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Codage d’une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)