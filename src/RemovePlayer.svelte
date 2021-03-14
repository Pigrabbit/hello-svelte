<script>
import { createEventDispatcher } from "svelte";


  const dispatch = createEventDispatcher();
  const onSubmit = (e) => {
    e.preventDefault();
    dispatch("removePlayer")
  }
</script>

<form on:submit={onSubmit}>
  <input type="submit" class="btn btn-primary" value="remove" />
</form>
