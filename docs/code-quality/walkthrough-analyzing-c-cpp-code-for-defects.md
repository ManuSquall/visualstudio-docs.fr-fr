---
title: 'Procédure pas à pas : analyse du code C/C++ pour rechercher les erreurs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6e15c6acc241e36e7cadc1d6f043549f1f5e46c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922031"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : analyse du code C/C++ pour rechercher les erreurs

Cette procédure pas à pas montre comment analyser du code C/C++ pour les erreurs potentielles de code à l’aide de l’outil d’analyse du code pour le code C/C++.

- Exécuter l’analyse du code sur le code natif.
- Analyser les avertissements d’erreur de code.
- Traiter l’avertissement comme une erreur.
- Annoter le code source pour améliorer l’analyse des erreurs de code.

## <a name="prerequisites"></a>Prérequis

- Une copie de la [exemple de démonstration](../code-quality/demo-sample.md).
- Compréhension de base de C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur le code natif

1. Ouvrez la solution de démonstration dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     À présent dans la solution de démonstration **l’Explorateur de solutions**.

2. Sur le **générer** menu, cliquez sur **régénérer la Solution**.

     La solution se génère sans aucun avertissement ni erreur.

3. Dans **l’Explorateur de solutions**, sélectionnez le projet CodeDefects.

4. Dans le menu **Projet**, cliquez sur **Propriétés**.

     Le **les Pages de propriétés de CodeDefects** boîte de dialogue s’affiche.

5. Cliquez sur **l’analyse du Code**.

6. Cliquez sur le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.

7. Régénérez le projet CodeDefects.

     Avertissements d’analyse du code sont affichent dans le **liste d’erreurs**.

### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements d’erreur de code

1. Sur le **vue** menu, cliquez sur **liste d’erreurs**.

     Selon le profil de développeur que vous avez choisi dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devrez peut-être pointer vers **autres fenêtres** sur la **vue** menu, puis sur **liste d’erreurs**.

2. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6230 : cast implicite entre types sémantiquement différents : utilisation de HRESULT dans un contexte Boolean.

     L’éditeur de code affiche la ligne qui a provoqué l’avertissement dans la fonction `bool``ProcessDomain()`. Cet avertissement indique qu’une valeur HRESULT est utilisé dans une instruction 'if' où un résultat booléen est attendu.

3. Corriger cet avertissement à l’aide de la macro SUCCEEDED. Votre code doit ressembler au code suivant :

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6282 : opérateur Incorrect : attribution de constante dans un contexte de test. == Est-il intentionnel ?

5. Corriger cet avertissement en testant l’égalité. Votre code doit ressembler au code suivant :

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Pour traiter un avertissement comme une erreur

1. Dans le fichier Bug.cpp, ajoutez le code suivant `#pragma` instruction au début du fichier à traiter l’avertissement C6001 comme une erreur :

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Régénérez le projet CodeDefects.

     Dans le **liste d’erreurs**, C6001 apparaît maintenant comme une erreur.

3. Corrigez les deux erreurs C6001 restantes dans le **liste d’erreurs** en initialisant `i` et `j` à 0.

4. Régénérez le projet CodeDefects.

     Le projet se génère sans les avertissements ou erreurs.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation.c

1. Dans l’Explorateur de solutions, sélectionnez le projet Annotations.

2. Dans le menu **Projet**, cliquez sur **Propriétés**.

     Le **les Pages de propriétés de Annotations** boîte de dialogue s’affiche.

3. Cliquez sur **l’analyse du Code**.

4. Sélectionnez le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.

5. Régénérez le projet Annotations.

6. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6011 : déréférencement du pointeur NULL 'newNode'.

     Cet avertissement indique que l’appelant pour vérifier la valeur de retour. Dans ce cas, un appel à **AllocateNode** peut retourner une valeur NULL (voir le fichier d’en-tête annotations.h la déclaration de fonction d’AllocateNode).

7. Ouvrez le fichier annotations.cpp.

8. Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Régénérez le projet Annotations.

     Le projet se génère sans les avertissements ou erreurs.

### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source

1. Annotez les paramètres formels et la valeur de retour de la fonction `AddTail` en utilisant les conditions Pre et Post comme indiqué dans cet exemple :

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Régénérez le projet Annotations.

3. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6011 : suppression de référence un pointeur NULL 'nœud'.

     Cet avertissement indique que le nœud passé dans la fonction peut être null et indique le numéro de ligne où l’avertissement a été déclenché.

4. Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Régénérez le projet Annotations.

     Le projet se génère sans les avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Analyse du Code managé pour les erreurs de Code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[l’analyse du Code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)