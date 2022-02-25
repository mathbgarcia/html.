<!-- Eu optei por usar uma estrutura de tailwindcss para mim auxiliar a codar. 
Um vento de cauda é prática, simples e facil de aprender. Apesar de não 
dominar a ferramenta já pude fazer uso dela -->

<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet" />

<!-- Vamos ao HTML5. Uma tag <div> é usada como um contêiner para os elementos HMTL, que pode ser usado depois pelo CSS ou pelo Javascript -->

<div class="h-100 w-full flex items-centro justify-center bg-teal-lightest font-sans mt-20">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
        <div class="mb-4">
            <h1 class="text-3xl md:text-4xl text-indigo-600 font-medium mb-2">Lista de Tarefas</h1>
            <classe div="flex mt-4">
                <classe de entrada="sombra aparência-nenhuma borda arredondada w-full py-2 px-3 mr-4 text-grey-darker" name="text" id="text" placeholder="Adicionar Tarefa" />
                <tipo de entrada="oculta" id="salvarIndex" />
                <classe de botão="p-2 lg:px-4 md:mx-2 text-center border-solid border-indigo-600 rounded text-white bg-indigo-600 transition-colors duração-300 mt-1 md:mt-0 md:ml-1" id="botao-add-tarefa">Add</button/button>
                <classe button="p-2 lg:px-4 md:mx-2 text-center border-solid border-indigo-600 arredondado bg-indigo-600 text-white transition-colors duração-300 mt-1 md:mt-0 md:ml-1" style="display: none" id="botao-salvar-tarefa">Editar Tarefa</button>
            </div>
        </div>
        <div id="listBox"></div>
    </div>
</div>

<roteiro>

    texto var  = documento. getElementById ("texto");
    var addTaskButton = documento. getElementById ("botao-add-tarefa");
    var saveTaskButton = documento. getElementById("botao-salvar-tarefa");
    var listBox = documento. getElementById ("listBox");
    var saveInd = documento. getElementById ("saveIndex");

        deixe todoArray = [];

        addTaskButton. addEventListener("clique", (e) => {
            e. prevenirDefault();
            deixe todo = localStorage. getItem("todo");
                se (todo === nulo) {
                    todoArray = [];
                } mais {
                    todoArray = JSON. parse (todo);
        }
        todoArray. push (texto. valor);
        texto. valor = "";
        localidadeStorage. setItem("todo", JSON. stringify (todoArray));
        displayTodo();
        });

            exibição de funçãoTodo() {
                deixe todo = localStorage. getItem("todo");
                se (todo === nulo) {
                    todoArray = [];
                } mais {
                    todoArray = JSON. parse (todo);
            }

            deixe htmlCode = "";
                todoArray. forEach(lista, ind) => {
                htmlCode += '<div class='flex mb-4 items-center'>
                            <p class='w-full text-grey-darkest'>${list}</p>
                            <button onclick='edit(${ind})' class='flex-no-shrink p-2 ml-4 mr-2 border-2 rounded text-white text-grey bg-green-600'>Edit</button>
 <butto onclick='deleteTodo(${ind})' class='flex-no-shrink p-2 ml-2 border-2 rounded text-white bg-red-500'>Feito</button>
 </div>';
            });

                listBox. innerHTML = htmlCode;
           
            }


            função deleteTodo (ind) {
                deixe todo = localStorage. getItem("todo");
                todoArray = JSON. parse (todo);
                todoArray. emenda (ind, 1);
                localidadeStorage. setItem("todo", JSON. stringify (todoArray));
            displayTodo();
            }

                edição de função (ind) {
                    salvarInd. valor = ind;
                    deixe todo = localStorage. getItem("todo");
                    todoArray = JSON. parse (todo);
                    texto. valor = todoArray[ind];
                    addTaskButton. estilo. display = "nenhum";
                    salvarTaskButton. estilo. display = "bloco";
                }
                
                salvarTaskButton. addEventListener ("clique", () => {
                    deixe todo = localStorage. getItem("todo");
                        todoArray = JSON. parse (todo);
                    deixe id = saveInd. valor;
                         todoArray[id] = texto. valor;
                         addTaskButton. estilo. display = "bloco";
                         salvarTaskButton. estilo. display = "nenhum";
                         texto. valor = "";
                         localidadeStorage. setItem("todo", JSON. stringify (todoArray));
                    displayTodo();
                });
</roteiro>
