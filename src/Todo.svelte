
    <script>
        import Popover from "svelte-popover";
    </script>
  
  <Popover arrowColor="#fff">
    <span slot="target">Todo</span>
    <div id="content" slot="content" class="content">Content</div>
  </Popover>
  <style>
      #content {
        background: black;
    color: white;
}
  </style>