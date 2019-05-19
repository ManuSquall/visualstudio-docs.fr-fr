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
ms.openlocfilehash: b81bd810bac142bdec23074e69bbd3840043c8f6
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841408"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003 : Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Entrée de demande HTTP potentiellement non fiable atteint le chemin d’accès d’une opération de fichier.

## <a name="rule-description"></a>Description de la règle

Lorsque vous travaillez avec des entrées non approuvées des requêtes web, tenez compte de l’aide des entrées de contrôlée par l’utilisateur lors de la spécification de chemins d’accès aux fichiers. Une personne malveillante peut être en mesure de lire un fichier involontaire, ce qui entraîne la divulgation d’informations des données sensibles. Ou bien, une personne malveillante peut être en mesure d’écrire dans un fichier involontaire, ce qui entraîne une modification non autorisée des données sensibles ou compromettre la sécurité du serveur. Est une technique courante de la personne malveillante [traversée de chemin d’accès](https://www.owasp.org/index.php/Path_Traversal) pour accéder aux fichiers en dehors du répertoire souhaité.

Cette règle tente de trouver des informations issues de requêtes HTTP atteindre un chemin d’accès dans une opération de fichier.

> [!NOTE]
> Cette règle ne peut pas suivre les données entre les assemblys. Par exemple, si un seul assembly lit l’entrée de demande HTTP et le transmet ensuite à un autre assembly qui écrit dans un fichier, cette règle ne génère un avertissement.

> [!NOTE]
> Il existe une limite configurable pour la profondeur cette règle permet d’analyser les flux de données entre les appels de méthode. Consultez [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) pour savoir comment configurer la limite dans un fichier EditorConfig.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Si possible, limitez les chemins de fichiers basées sur l’entrée d’utilisateur à une liste verte explicitement connue.  Par exemple, si votre application a besoin uniquement d’accéder à « red.txt », « green.txt » ou « blue.txt », autoriser uniquement ces valeurs.
- Vérifiez les noms de fichiers non approuvés et valider que le nom est correct.
- Utilisez des noms de chemin d’accès complet lors de la spécification de chemins d’accès.
- Évitez les constructions potentiellement dangereuses telles que les variables d’environnement path.
- Uniquement accepter les noms de fichiers longs et valider le nom long si l’utilisateur soumet des noms courts.
- Limiter l’entrée d’utilisateur final pour les caractères valides.
- Rejeter les noms de cas de dépassement de longueur MAX_PATH.
- Gérer les noms de fichiers littéralement, sans interprétation.
- Déterminer si le nom de fichier représente un fichier ou un périphérique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si vous avez validé entrée comme décrit dans la section précédente, il est OK supprimer cet avertissement.

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
