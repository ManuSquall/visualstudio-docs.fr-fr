---
title: Procédure pas à pas d’analyse du code managé pour les erreurs de code | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547999"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Procédure pas à pas : Utiliser l’analyse statique du code pour rechercher les erreurs de code

Dans cette procédure pas à pas, vous allez analyser un projet managé pour les erreurs de code à l’aide de l’analyse du code hérité.

Cet article vous guide tout au long du processus d’utilisation de l’analyse héritée pour analyser vos assemblys de code managé .NET en conformité avec les règles de conception de .NET.

## <a name="create-a-class-library"></a>Créer une bibliothèque de classes

### <a name="to-create-a-class-library"></a>Pour créer une bibliothèque de classes

1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **nouveau projet** , développez**Visual C#**  **installé** > , puis choisissez **Bureau Windows**.

1. Choisissez le modèle **bibliothèque de classes (.NET Framework)** .

1. Dans la zone de texte **nom** , tapez **CodeAnalysisManagedDemo** , puis cliquez sur **OK**.

1. Une fois le projet créé, ouvrez le fichier *Class1.cs* .

1. Remplacez le texte existant dans Class1.cs par le code suivant:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Enregistrez le fichier Class1.cs.

## <a name="analyze-the-project"></a>Analyser le projet

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Pour analyser un projet managé pour les erreurs de code

1. Sélectionnez le projet CodeAnalysisManagedDemo dans **Explorateur de solutions**.

1. Dans le menu **Projet**, cliquez sur **Propriétés**.

     La page de propriétés CodeAnalysisManagedDemo s’affiche.

1. Choisissez l’onglet **analyse du code** .

1. Assurez-vous que l’option **activer l’analyse du code sur la build** est cochée.

1. Dans la liste déroulante **exécuter cet ensemble de règles** , sélectionnez **toutes les règles Microsoft**.

1. Dans le menu **fichier** , cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.

1. Dans le menu **générer** , cliquez sur **générer CodeAnalysisManagedDemo**.

    Les avertissements de génération de projet CodeAnalysisManagedDemo s’affichent dans les fenêtres de **liste d’erreurs** et de **sortie** .

## <a name="correct-the-code-analysis-issues"></a>Corriger les problèmes liés à l’analyse du code

### <a name="to-correct-code-analysis-rule-violations"></a>Pour corriger les violations des règles d’analyse du code

1. Dans le menu **affichage** , choisissez **liste d’erreurs**.

    En fonction du profil de développeur que vous avez choisi, vous devrez peut-être pointer sur **autres fenêtres** dans le menu **affichage** , puis choisir **liste d’erreurs**.

1. Dans l’**Explorateur de solutions**, choisissez **Afficher tous les fichiers**.

1. Développez le nœud Propriétés, puis ouvrez le fichier *AssemblyInfo.cs* .

1. Utilisez les conseils suivants pour corriger les avertissements:

   [CA1014 Marquer les assemblys avec](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)CLSCompliantAttribute: Microsoft. Design: «Demo» doit être marqué avec CLSCompliantAttribute et sa valeur doit être true.

   1. Ajoutez le code `using System;` au fichier AssemblyInfo.cs.

   1. Ensuite, ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.

   [CA1032 Implémenter des constructeurs](../code-quality/ca1032-implement-standard-exception-constructors.md)d’exception standard: Microsoft. Design: Ajoutez le constructeur suivant à cette classe: Demo public (String)

   1. Ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo`.

   [CA1032 Implémenter des constructeurs](../code-quality/ca1032-implement-standard-exception-constructors.md)d’exception standard: Microsoft. Design: Ajoutez le constructeur suivant à cette classe: Demo public (String, exception)

   1. Ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo`.

   [CA1032 Implémenter des constructeurs](../code-quality/ca1032-implement-standard-exception-constructors.md)d’exception standard: Microsoft. Design: Ajoutez le constructeur suivant à cette classe: Demo protected demo (SerializationInfo, StreamingContext)

   1. Ajoutez le code `using System.Runtime.Serialization;` au début du fichier Class1.cs.

   1. Ensuite, ajoutez le constructeur`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032 Implémenter des constructeurs](../code-quality/ca1032-implement-standard-exception-constructors.md)d’exception standard: Microsoft. Design: Ajoutez le constructeur suivant à cette classe: Demo public ()

   1. Ajoutez le constructeur `public demo () : base() { }` à la classe `demo` **.**

   [CA1709 La casse des identificateurs doit être](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)correcte: Microsoft. Naming: Corrigez la casse du nom d’espace de noms «testCode» en le remplaçant par «TestCode».

   1. Remplacez la casse de l’espace `testCode` de `TestCode`noms par.

   [CA1709 La casse des identificateurs doit être](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)correcte: Microsoft. Naming: Corrigez la casse du nom de type «Demo» en le remplaçant par «demo».

   1. Remplacez le nom du membre par `Demo`.

   [CA1709 La casse des identificateurs doit être](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)correcte: Microsoft. Naming: Corrigez la casse du nom de membre «Item» en le remplaçant par «Item».

   1. Remplacez le nom du membre par `Item`.

   [CA1710 Les identificateurs doivent avoir le](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)suffixe correct: Microsoft. Naming: Renommez «testCode. demo» pour qu’il se termine par «exception».

   1. Remplacez le nom de la classe et ses constructeurs par `DemoException`.

   [CA2210 Les assemblys doivent avoir des noms](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)forts valides: Signez’CodeAnalysisManagedDemo’avec une clé de nom fort.

   1. Dans le menu **projet** , choisissez **Propriétés de CodeAnalysisManagedDemo**.

      Les propriétés du projet s’affichent.

   1. Choisissez l'onglet **Signature** .

   1. Activez la case à cocher **signer l’assembly** .

   1. Dans la liste **choisir un fichier de clé de nom de chaîne** , sélectionnez  **\<nouveau... >** .

      La boîte de dialogue **créer une clé de nom fort** s’affiche.

   1. Dans le **nom du fichier de clé**, tapez TestKey.

   1. Entrez un mot de passe, puis choisissez **OK**.

   1. Dans le menu **fichier** , sélectionnez **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.

   [CA2237 : Marquer les types ISerializable avec](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)SerializableAttribute: Microsoft. usage: Ajoutez un attribut [Serializable] au type «Demo», car ce type implémente ISerializable.

   1. Ajoutez l' `[Serializable ()]` attribut à la classe `demo`.

   Une fois les modifications terminées, le fichier Class1.cs doit ressembler à ce qui suit:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Regénérez le projet.

## <a name="exclude-code-analysis-warnings"></a>Exclure les avertissements d’analyse du code

1. Pour chacun des avertissements restants, procédez comme suit:

    1. Sélectionnez l’avertissement dans la **liste d’erreurs**.

    1. Dans le menu contextuel (menu contextuel), choisissez **supprimer** > **dans le fichier de suppression**.

1. Regénérez le projet.

     Le projet est généré sans avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Analyse du code managé](../code-quality/code-analysis-for-managed-code-overview.md)