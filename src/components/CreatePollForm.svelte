<script>
    import PollStore from '../store/PollStore';
    import {createEventDispatcher} from 'svelte';
    import Button from "../shared/Button.svelte";

    let fields = {question:'',answerA:'',answerB:''};
    let errors = {question:'',answerA:'',answerB:''};
    let valid = false;
    let dispatch = createEventDispatcher();

    const submitHandler = () => {
        valid = true;

        //validate question
        if (fields.question.trim().length < 5){
            valid = false;
            errors.question = 'Question must be at least 5 characters long!!';
        } else {
            errors.question = '';
        }

        //validate answer A
        if (fields.answerA.trim() < 1){
            valid = false;
            errors.answerA = 'Answer A cannot be empty!!';
        } else {
            errors.answerA = '';
        }

        //validate answer B
        if (fields.answerB.trim() < 1){
            valid = false;
            errors.answerB = 'Answer B cannot be empty!!';
        } else {
            errors.answerB = '';
        }

        //add new poll
        if (valid) {
            let poll = {...fields, voteA: 0, voteB: 0, id: Math.random()};
            //save poll to store
            PollStore.update(currentPolls => {
                return [poll, ...currentPolls];
            })
            dispatch('add');
        }
    };
</script>

<form on:submit|preventDefault={submitHandler}>
    <div class="form-field">
        <label for="question">Poll Question</label>
        <input type="text" id="question" bind:value={fields.question}>
        <div class="error">{errors.question}</div>
    </div>
    <div class="form-field">
        <label for="answer-a">Answer A</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
        <div class="error">{errors.answerA}</div>
    </div>
    <div class="form-field">
        <label for="answer-b">Answer B</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
        <div class="error">{errors.answerB}</div>
    </div>
    <Button type="secondary" flat={true}>Add Poll</Button>
</form>

<style>
    form{
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }
    .form-field{
        margin: 10px auto;
    }
    input{
        width: 100%;
        border-radius: 6px;
    }
    label{
        margin: 10px auto;
        text-align: left;
    }
    .error{
        font-weight: 400;
        font-size: 12px;
        color: #d91b42;
    }
</style>