# MotionLayout + RecyclerView

Primeiramente adicione as dependências no **build.gradle**

    implementation 'androidx.constraintlayout:constraintlayout:2.0.0-beta4'
    implementation 'androidx.recyclerview:recyclerview:1.1.0'

O `MotionLayout` é uma subclasse do `ConstraintLayout` que está disponível na sua versão 2.0, que no momento encontra-se em versão beta.

### Edição

Nesta seção explicarei um pouco referente MotionLayout.

- **_res/xml/main_scroll.xml_**

    Para realizar a animação da tela utilizando o `MotionLayout` criei um aquivo no diretório acima no projeto, e definir nele como o layout deve ficar após (ou durante) uma determinada ação.

	Primeiramente definimos uma `Transition` com uma duração de 1 segundo. As constraints de início terão o id `start`, e as de fim, o id `end`.  `OnSwipe` é onde indicamos que a animação será realizada durante um gesto de swipe para cima (`dragDirection`) usando como referência a parte superior (`anchorSide`).

	`ConstraintSet` como próprio nome sugere, define um conjunto de constraints para o layout. O conjunto inicial com o id `start` apenas indica que os dois componentes `TextView` ficarão visíveis (`alpha` igual a 1).

	`ConstraintSet` é que fará todas as mudanças de constraints para a animação. O `ImageView` é redimensionado e uma elevação é atribuída a ele. Essa elevação também será usada na nossa "fake toolbar" (a view `vwToolbar`). Para os dois `TextView` além do reposicionamento, é definida uma altura fixa de 16dp. Como o tamanho do texto está usando o recurso de _autosizing_, a animação é feita automaticamente.

### Dica

Uma dica que pode ser útil durante o desenvolvimento de animações com o `MotionLayout` é ativar a propriedade `showPaths`. Ela mostrará o caminho que está sendo realizado pelos componentes durante a animação.

    <androidx.constraintlayout.motion.widget.MotionLayout 
	    ...  
	    app:showPaths="true">

