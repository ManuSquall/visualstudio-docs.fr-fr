---
title: Créer une règle de validation personnalisée pour un test de performances Web
description: Découvrez comment créer vos propres règles de validation, dérivées d’une classe de règles de validation, ValidationRule.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ae5228c4da9abef9b5bee417d5d3d71bb28d416d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964587"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Coder une règle de validation personnalisée pour un test de performances web

Vous pouvez créer vos propres règles de validation. Pour cela, vous dérivez votre propre classe de règles à partir d'une classe de règles de validation. Les règles de validation dérivent de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>.

> [!NOTE]
> Il est également possible de créer vos propres règles d'extraction personnalisées. Pour plus d’informations, consultez [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>Pour créer des règles de validation personnalisées

1. Ouvrez un projet de test qui contient un test de performances de site web.

2. (Facultatif) Créez un projet de bibliothèque de classes distinct dans lequel stocker votre règle de validation.

    > [!IMPORTANT]
    > Vous pouvez créer la classe dans le projet qui contient vos tests. Toutefois, si vous souhaitez réutiliser la règle, il est préférable de créer un projet de bibliothèque de classes distinct pour la stocker. Si vous créez un projet séparé, vous devez compléter les étapes facultatives dans cette procédure.

3. (Facultatif) Dans le projet de bibliothèque de classes, ajoutez une référence à la DLL Microsoft.VisualStudio.QualityTools.WebTestFramework.

4. Créez une classe qui dérive de la classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Implémentez les membres <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>.

5. (Facultatif) Générez le nouveau projet de bibliothèque de classes.

6. (Facultatif) Dans le projet de test, ajoutez une référence au projet de bibliothèque de classes qui contient la règle de validation personnalisée.

7. Dans le projet de test, ouvrez un test de performances de site Web dans la **éditeur de test de performances Web**.

8. Pour ajouter la règle de validation personnalisée à une requête de test de performances de site Web, cliquez avec le bouton droit sur une demande, puis sélectionnez **Ajouter une règle de validation**.

     La boîte de dialogue **Ajouter une règle de validation** s’affiche. Votre règle de validation personnalisée apparaît dans la liste **Sélectionner une règle** avec les règles de validation prédéfinies. Sélectionnez votre règle de validation personnalisée, puis choisissez **OK**.

9. Exécutez votre test de performances web.

## <a name="example"></a>Exemple

Le code suivant illustre une implémentation d'une règle de validation personnalisée. Cette règle de validation reproduit le comportement de la règle de validation prédéfinie Étiquette obligatoire. Utilisez cet exemple comme point de départ pour la définition de vos propres règles de validation personnalisées.

> [!WARNING]
> Les propriétés publiques du code d'un validateur personnalisé ne peuvent pas avoir de valeurs Null.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Codage d'une règle d'extraction personnalisée pour un test de performances de site Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
