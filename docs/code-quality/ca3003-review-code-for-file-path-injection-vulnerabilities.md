---
title: 'CA3003 : Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9e43dcdf1e923cb7bc4a98b17fd0be71b7927eb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237399"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003 : Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une entrée de requête HTTP potentiellement non approuvée atteint le chemin d’accès d’une opération de fichier.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées à partir de requêtes Web, pensez à utiliser une entrée contrôlée par l’utilisateur lors de la spécification des chemins d’accès aux fichiers. Une personne malveillante peut être en mesure de lire un fichier involontaire, entraînant la divulgation d’informations de données sensibles. Ou bien, une personne malveillante peut être en mesure d’écrire dans un fichier involontaire, entraînant une modification non autorisée des données sensibles ou une compromission de la sécurité du serveur. Une technique d’attaque courante consiste à [Parcourir les chemins](https://www.owasp.org/index.php/Path_Traversal) d’accès pour accéder aux fichiers en dehors du répertoire prévu.

Cette règle tente de trouver une entrée à partir de requêtes HTTP qui atteignent un chemin d’accès dans une opération de fichier.

> [!NOTE]
> Cette règle ne peut pas effectuer le suivi des données dans les assemblys. Par exemple, si un assembly lit l’entrée de la requête HTTP, puis le passe à un autre assembly qui écrit dans un fichier, cette règle ne génère pas d’avertissement.

> [!NOTE]
> Il existe une limite configurable de la profondeur de cette règle pour analyser le workflow des données entre les appels de méthode. Consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier baEditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, limitez les chemins de fichiers en fonction de l’entrée utilisateur dans une liste approuvée explicitement.  Par exemple, si votre application doit uniquement accéder à « Red. txt », « Green. txt » ou « Blue. txt », autorisez uniquement ces valeurs.
- Vérifiez les noms de fichiers non approuvés et vérifiez que le nom est bien formé.
- Utilisez les noms de chemin d’accès complets lorsque vous spécifiez des chemins.
- Évitez les constructions potentiellement dangereuses telles que les variables d’environnement PATH.
- Accepter uniquement les noms de fichiers longs et valider le nom long si l’utilisateur envoie des noms courts.
- Limitez l’entrée de l’utilisateur final aux caractères valides.
- Rejette les noms dont la longueur MAX_PATH est dépassée.
- Gérer les noms de fichiers littéralement, sans interprétation.
- Déterminez si le nom de fichier représente un fichier ou un périphérique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous avez validé l’entrée comme décrit dans la section précédente, il est possible de supprimer cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is:
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display
            // The content to the webpage.
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is:
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display
            ' The content to the webpage.
        End Using
    End Sub
End Class
```
