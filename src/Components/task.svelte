<script>
    export let taskName = "Error";
    export let taskId = "0";
</script>

<span class="task" id={taskId}>
    <span class="taskName">
        <div >{taskId}. {taskName}</div>
    </span>
    <span class="taskMove"><i class="fas fa-grip-lines"></i></span>
    <span class="taskRemove">X</span>
</span>

<style>
    .task {
        background-color: #444444;
        color: white;
        border-radius: 5px;
        width: 100%;
        margin-top: 7px;
        margin-bottom: 7px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: large;
    }

    .task:hover {
        background-color: #555555;
        cursor: grab;
    }

    .task:active {
        background-color: #666666;
        cursor: grabbing;
    }

    .task:hover .taskRemove {
        opacity: 100%;
        width: 40px;
    }

    .task:hover .taskMove {
        opacity: 100%;
        width: 40px;
        cursor: grab;
    }

    .task:active .taskMove {
        cursor: grabbing;
    }

    .taskName {
        height: 100%;
        padding: 7px 7px;
    }

    .taskMove {
        opacity: 0%;
        width: 40px;
        height: 100%;
        border-radius: 5px;
        cursor: pointer;
        padding: 7px 7px;
        color: rgba(255, 255, 255, 0.541);
    }

    .taskRemove {
        opacity: 0%;
        text-align: center;
        background-color: rgba(255, 255, 255, 0.164);
        border-radius: 5px;
        padding: 7px 7px;
        color: #fff;
        font-weight: bolder;
        height: 100%;
        cursor: pointer;
    }

    .taskRemove:hover {
        background-color: #fd6464;
        cursor: pointer;
    }

    .taskRemove:active {
        background-color: #ffc8c8;
        cursor: pointer;
    }

</style>