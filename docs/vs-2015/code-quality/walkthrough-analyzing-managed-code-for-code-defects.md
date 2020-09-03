---
title: 'Procédure pas à pas : analyse du code managé pour les erreurs de code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609330"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procédure pas à pas : analyse du code managé pour les erreurs de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous analysez un projet managé pour les erreurs de code à l’aide de l’outil d’analyse du code.

 Cette procédure pas à pas vous guidera tout au long du processus d’utilisation de l’analyse du code pour analyser vos assemblys de code managé .NET en conformité avec les règles de conception de la Microsoft .NET Framework.

 Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :

- Analyser et corriger les avertissements de défaut de code.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Créer une bibliothèque de classes

#### <a name="to-create-a-class-library"></a>Pour créer une bibliothèque de classes

1. Dans le menu **fichier** de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , cliquez sur **nouveau** , puis sur **projet**.

2. Dans la boîte de dialogue **nouveau projet** , sous **types de projets**, cliquez sur **Visual C#**.

3. Sous **Modèles**, sélectionnez **Bibliothèque de classes**.

4. Dans la zone de texte **nom** , tapez **CodeAnalysisManagedDemo** , puis cliquez sur **OK**.

5. Une fois le projet créé, ouvrez le fichier Class1.cs.

6. Remplacez le texte existant dans Class1.cs par le code suivant :

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Enregistrez le fichier Class1.cs.

## <a name="analyze-the-project"></a>Analyser le projet

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Pour analyser un projet managé pour les erreurs de code

1. Sélectionnez le projet CodeAnalysisManagedDemo dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Propriétés**.

     La page de propriétés CodeAnalysisManagedDemo s’affiche.

3. Cliquez sur **CodeAnalysis**.

4. Assurez-vous que l’option  **activer l’analyse du code sur la build (définit CODE_ANALYSIS constante**) est cochée.

5. Dans la liste déroulante **exécuter cet ensemble de règles** , sélectionnez **toutes les règles Microsoft**.

6. Dans le menu **fichier** , cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés ManagedDemo.

7. Dans le menu **générer** , cliquez sur **Générer ManagedDemo**.

     Les avertissements de génération du projet CodeAnalysisManagedDemo sont signalés dans les fenêtres **analyse du code** et **sortie** .

     Si la fenêtre **analyse du code** n’apparaît pas, dans le menu **analyser** , choisissez **fenêtres** , puis analyse du **code**.

## <a name="correct-the-code-analysis-issues"></a>Corriger les problèmes liés à l’analyse du code

#### <a name="to-correct-code-analysis-rule-violations"></a>Pour corriger les violations des règles d’analyse du code

1. Dans le menu **Affichage** , cliquez sur **Liste d'erreurs**.

     En fonction du profil de développeur que vous avez choisi, vous devrez peut-être pointer sur **autres fenêtres** dans le menu **affichage** , puis cliquez sur **liste d’erreurs**.

2. Dans **Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**.

3. Ensuite, développez le nœud Propriétés, puis ouvrez le fichier AssemblyInfo.cs.

4. Pour corriger les avertissements, utilisez la commande suivante :

- [CA1014 : marquer les assemblys avec CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design : « Demo » doit être marqué avec CLSCompliantAttribute, et sa valeur doit être true.

  - Ajoutez le code `using``System;` au fichier AssemblyInfo.cs.

       Ensuite, ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.

       Regénérez le projet.

- [CA1032 : implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design : ajoutez le constructeur suivant à cette classe : Demo public (String)

  - Ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo` .

- [CA1032 : implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design : ajoutez le constructeur suivant à cette classe : Demo public (String, exception)

  - Ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo` .

- [CA1032 : implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design : ajoutez le constructeur suivant à cette classe : Demo protected demo (SerializationInfo, StreamingContext)

  - Ajoutez le code `using System.Runtime.Serialization;` au début du fichier Class1.cs.

       Ensuite, ajoutez le constructeur `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Regénérez le projet.

- [CA1032 : implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design : ajoutez le constructeur suivant à cette classe : Demo public ()

  - Ajoutez le constructeur `public demo () : base() { }` à la classe `demo` **.**

       Regénérez le projet.

- [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming : corrigez la casse du nom d’espace de noms’testCode’en le remplaçant par’testCode'.

  - Remplacez la casse de l’espace de noms `testCode` par `TestCode` .

- [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming : corrigez la casse du nom de type « Demo » en le remplaçant par « demo ».

  - Remplacez le nom du membre par `Demo` .

- [CA1709 : la casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming : corrigez la casse du nom de membre’Item’en le remplaçant par’Item'.

  - Remplacez le nom du membre par `Item` .

- [CA1710 : les identificateurs doivent avoir le suffixe correct](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming : Rename’TestCode. Demo’pour se terminer par’exception'.

  - Remplacez le nom de la classe et ses constructeurs par `DemoException` .

- [CA2210 : les assemblys doivent avoir des noms forts valides](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): signez’ManagedDemo’avec une clé de nom fort.

  - Dans le menu **projet** , cliquez sur **Propriétés ManagedDemo**.

       Les propriétés du projet s’affichent.

       Cliquez sur **signature**.

       Activez la case à cocher **signer l’assembly** .

       Dans la liste **choisir un fichier de clé de nom de chaîne** , sélectionnez **\<New…>** .

       La boîte de dialogue **Créer une clé de nom fort** s'affiche.

       Dans le **nom du fichier de clé**, tapez TestKey.

       Entrez un mot de passe, puis cliquez sur **OK**.

       Dans le menu **fichier** , cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.

       Regénérez le projet.

- [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. usage : ajoutez un attribut [Serializable] au type « Demo », car ce type implémente ISerializable.

  - Ajoutez l' `[Serializable ()]` attribut à la classe `demo` .

       Regénérez le projet.

  Une fois les modifications terminées, le fichier Class1.cs doit ressembler à ce qui suit :

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Exclure les avertissements d’analyse du code

#### <a name="to-exclude-code-defect-warnings"></a>Pour exclure les avertissements liés aux défauts de code

1. Pour chacun des avertissements restants, procédez comme suit :

   1. Dans la fenêtre analyse du code, sélectionnez l’avertissement.

   2. Choisissez **actions**, puis **supprimer le message**, puis choisissez **dans le fichier de suppression du projet**.

      Pour plus d’informations, consultez [Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Regénérez le projet.

    Le projet est généré sans avertissements ou erreurs.
