---
title: "Démarrage rapide : Créer un projet Python à partir d’un modèle dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: quickstart
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 87fdca001430acc1ecef7e69b9afc2123dedafd0
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Démarrage rapide : Créer un projet Python à partir d’un modèle dans Visual Studio

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2017](installation.md), il est facile de créer un projet Python avec une large gamme de modèles.

1. Lancez Visual Studio.

1. Sélectionnez **Fichier > Nouveau > Projet** (Ctrl+Maj+N). Dans la boîte de dialogue **Nouveau projet**, recherchez « Python » et sélectionnez le modèle souhaité. Notez que la sélection d’un modèle affiche une brève description de ce que le modèle fournit. (Consultez aussi [Projets Python](python-projects.md#project-templates).)

    ![Boîte de dialogue Nouveau projet de Visual Studio 2017 avec un modèle Python](media/projects-new-project-dialog2.png)

1. Pour ce démarrage rapide, sélectionnez le modèle « Application Python », donnez un nom (par exemple « MakePI ») et un emplacement au projet, puis sélectionnez **OK**. 

1. Visual Studio crée le fichier projet (un fichier `.pyproj` sur le disque), ainsi que tous les autres fichiers décrits par le modèle. Avec le modèle « Application Python », le projet contient seulement un fichier vide qui a le même nom que votre projet. Le fichier est ouvert dans l’éditeur Visual Studio par défaut.

    ![Projet résultant lors de l’utilisation du modèle Application Python](media/projects-new-structure.png)

1. Ajoutez du code dans le fichier ouvert, par exemple le code ci-dessous, qui calcule et affiche 1000 décimales du nombre Pi :

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Exécutez le programme en appuyant sur Ctrl+F5 ou en sélectionnant **Déboguer > Démarrer sans débogage** dans le menu. Les résultats s’affichent dans une fenêtre de console.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Voir aussi

- [Création d’un environnement pour un interpréteur Python existant](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Installer la prise en charge de Python dans Visual Studio 2015 et antérieur](installation.md).
- [Emplacements d’installation](installation.md#install-locations).
